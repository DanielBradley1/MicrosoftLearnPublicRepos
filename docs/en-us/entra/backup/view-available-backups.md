<!-- Source: https://learn.microsoft.com/en-us/entra/backup/view-available-backups -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# View available backups in Microsoft Entra Backup and Recovery

This article describes how to view available backups for your tenant in Microsoft Entra Backup and Recovery.

Microsoft Entra backups provide a point-in-time view of supported tenant objects and their attributes. Backups help administrators review changes and recover from accidental or unwanted modifications.

Key characteristics of Backup and Recovery:

- **One backup per day**: Microsoft Entra automatically creates one backup each day for your tenant.
- **Retained for seven days**: Each backup is available for up to seven days from its timestamp.
- **Non-editable**: Backups can't be modified or deleted.

## Prerequisites

To view available backups in your tenant, you must have the **Microsoft Entra Backup Reader** role or a higher-privileged role.

## View backups

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a **Microsoft Entra Backup Reader**.
2. Browse to **Backup and recovery**. The **Overview** page shows feature highlights, alerts, and recent activity.

   ![Screenshot of the Backup and recovery Overview page in the Microsoft Entra admin center, showing feature highlights and alerts.](https://learn.microsoft.com/en-us/entra/backup/media/view-available-backups/backup-recovery-overview.png#lightbox)
3. Select **Backups** to view the list of available backups for your tenant. Each backup shows its timestamp and backup ID.

   ![Screenshot of the Backups page showing a list of five available backups with their timestamps and backup IDs.](https://learn.microsoft.com/en-us/entra/backup/media/view-available-backups/backups-list.png#lightbox)

From the **Backups** page, select a backup to [create a difference report](https://learn.microsoft.com/en-us/entra/backup/create-review-difference-reports) or [start a recovery](https://learn.microsoft.com/en-us/entra/backup/recover-objects).

## Related content

- [Create and review difference reports](https://learn.microsoft.com/en-us/entra/backup/create-review-difference-reports)
- [Recover objects](https://learn.microsoft.com/en-us/entra/backup/recover-objects)
