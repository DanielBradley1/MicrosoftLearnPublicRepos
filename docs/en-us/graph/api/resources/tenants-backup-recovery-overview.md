<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenants-backup-recovery-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Backup and recovery APIs in Microsoft Graph

Namespace: microsoft.graph

Backup and recovery APIs in Microsoft Graph let you programmatically protect and restore tenant data across Microsoft 365 services and Microsoft Entra directory objects. These APIs support business continuity scenarios such as recovering from ransomware attacks, accidental deletions, or security compromises.

Tip

This capability is part of [tenant management features available in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/tenants-overview).

Two capabilities are available:

- **Microsoft 365 Backup and Storage**—backs up and restores content in SharePoint sites, OneDrive accounts, and Exchange mailboxes.
- **Microsoft Entra Backup and Recovery**—backs up and restores critical Microsoft Entra directory objects such as users, groups, applications, service principals, and key policies.

## Microsoft 365 Backup and Storage

The Microsoft 365 Backup Storage APIs let you build applications to protect and restore content in SharePoint sites, OneDrive accounts, and Exchange mailboxes. The service retains backups for up to one year with recovery points every ten minutes, and restores are free—charges apply only to the storage of protected data. For licensing and pricing details, see [Microsoft 365 Backup pricing](https://www.microsoft.com/en-us/microsoft-365/microsoft-365-backup).

Using these APIs, your application can:

- Enable and configure the backup service
- Define protection policies for mailboxes, OneDrive accounts, and SharePoint sites
- Manage restore sessions to recover content to a known-good state
- Monitor the status of ongoing protection and restore operations

[Explore Microsoft 365 Backup Storage APIs](https://learn.microsoft.com/en-us/graph/api/resources/backuprestoreroot)

## Microsoft Entra Backup and Recovery

![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png)

The Microsoft Entra Backup and Recovery APIs let you programmatically back up and restore critical Microsoft Entra directory objects to a previously known good state. Microsoft Entra automatically creates one backup snapshot per day and retains up to five days of history.

Using these APIs, your application can:

- List available backup snapshots
- Run preview jobs to identify which objects would change before committing to a recovery
- Run recovery jobs to restore objects to a snapshot state
- Review any changes that couldn't be applied

[Discover API operations for Microsoft Entra Backup and Recovery](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-backup-recovery-overview)
