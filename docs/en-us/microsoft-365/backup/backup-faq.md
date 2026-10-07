<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Frequently asked questions about Microsoft 365 Backup

#### Has Microsoft's stance on shared responsibility of data protection changed?

No, we still have the same point of view, but are now offering more tools to help organizations achieve those goals and responsibilities.

#### Why don't Disaster Recovery copies suffice for my backup?

Disaster Recovery \(DR\) is the ability to recover from a situation in which the primary data center is unable to continue to operate. A DR copy with Microsoft 365 maintains the current state of content, not any historical versions from prior points in time. Microsoft 365 Backup offers the added advantage of allowing you to restore data to a previous healthy state quickly, with fast RTO \(recovery time objectives\) and short RPO \(recovery point objectives\).

#### Why don't versions already solve this point in time restore problem?

Versions give individual users a way to restore files or sites to prior points in time. However, that kind of recovery method doesn't scale well for large-scale ransomware attacks where an admin needs to orchestrate the recovery. Versions might also be exhausted depending on the version limit set by the admin.

#### Why don't legal holds solve the problem of keeping all versions of items for recovery?

Legal holds retain data, but that feature is optimized for export \(for example, via eDiscovery\), not for mass restore. Microsoft 365 Backup gives the right enhanced restore tooling for ransomware and accidental/malicious deletions at scale, plus optimized performance for those scenarios.

#### What mailbox changes are "backed up"?

Mailbox backup enables the recovery of copies of mailbox item "versions." Two types of actions create versions:

- Modifications
- Deletions

Example events that are versions and recoverable via backup:

**User action**

- Edit a received email using "edit message" via Outlook
- Edit a Note \(not draft\)
- Remove an attachment from an email
- Edit an attachment to an email
- Edit a contact \(not draft\)
- Modify body of a calendar invite
- Update time of a calendar invite
- Edit a task \(not draft\)
- Delete note from deleted items
- Delete email from deleted items
- Purge items from single item retention
- Delete a folder with items in it

Example events that aren't versioned or recoverable via backup:

**User action**

- Edit an email item in the drafts folder
- Update a flag on a received email
- Set "Do Not Forward" on a received email
- Set a received message to highly important

#### What is the service recovery point objective?

The recovery point objective \(RPO\) is the maximum amount of time between the most recent backup and a data destruction event. Stated another way, it's the amount data lost due to a data destruction event not recoverable via the backups. For Microsoft 365 Backup, the RPOs are:

- For OneDrive and SharePoint, the RPO for the trailing two weeks is 10 minutes. This means if it's Monday at 8:00 AM, you can go back in time to any 10-minute period up to two weeks in the past. Beyond two weeks, you can go to any one week period of time in past from 2 to 52 weeks in the past.
- For Exchange Online, the RPO is 10 minutes, meaning the most amount of data that can be lost due to a data destruction event is roughly 10 minutes' worth of data.

Let's start with what it doesn't mean: We're *not* taking snapshots every 10 minutes.

A backup frequency of 10 minutes means that all changes made to the item are saved as a new version every 10 minutes, regardless of how many changes occur within that 10-minute period. For example, if a ransomware attack encrypts the email item every minute, there are six copies made in an hour. The backup frequency does not apply to deletions. All deletions are backed up.

#### What happens when user content is backed up but then is removed or deleted from Microsoft Entra ID \(formerly Azure Active Directory\)?

When a user is removed from the backup policy, the backup of the OneDrive account or Exchange mailbox is retained for one year from the date the backup was created.

When a user is deleted from Microsoft Entra ID, the backup of the OneDrive account or Exchange mailbox is retained for one year from the date the backup was created.

When a site is removed from the backup policy, the backup of the SharePoint site is held for 52 weeks from the time a given restore point was created for that site.

#### How can I restore the OneDrive account or Exchange mailbox for a user who is deleted from Microsoft Entra ID \(formerly Azure Active Directory\)?

If the user was deleted within the past 30 days, the user is in a soft-deleted state. The best option is to recover the user based on instructions found at [Restore a user in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/restore-user). Once the user is recovered, the rest of the restore experience will work as normal.

For OneDrive, you can restore the OneDrive to the original URL or a new URL. At that time, the OneDrive is in an "orphaned" state. To connect the OneDrive to a user, see [Fix site user ID mismatch in SharePoint or OneDrive](https://learn.microsoft.com/en-us/sharepoint/troubleshoot/sharing-and-permissions/fix-site-user-id-mismatch).

For Exchange, if the user account is permanently/hard deleted, Microsoft 365 Backup retains the inactive mailbox while the backup policy remains in effect. To recover the inactive mailbox, follow the guidance at [Recover an inactive mailbox](https://learn.microsoft.com/en-us/purview/recover-an-inactive-mailbox) to convert the inactive mailbox to a new, active mailbox. Once the inactive mailbox is recovered, add the new user to the backup policy to access backups from the recovered mailbox. The original, now deleted user can then be removed from the backup policy. Only the [Recover an inactive mailbox](https://learn.microsoft.com/en-us/purview/recover-an-inactive-mailbox) process is supported. The [Restore an inactive mailbox](https://learn.microsoft.com/en-us/purview/restore-an-inactive-mailbox) process does not preserve the backup data from the old mailbox.

If you receive an error stating "The ExternalDirectoryObjectID of this inactive mailbox still exists," the user was deleted less than 30 days ago. In this case, restore the user based on instructions found at [Restore a user in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/restore-user).

#### If I transfer control of the Backup tool from the native first-party Microsoft 365 application to a third-party application built on the Microsoft 365 Backup Storage platform, can I revert control back to the first-party application at a later date?

Currently, you can only transfer control from the first-party Microsoft 365 application to a third-party application. We're actively working on an enhancement to allow transfers from third-party applications back to the first-party application. If you urgently need to transfer control from a third-party application to the first-party application, please file a support ticket.

#### Can I use PowerShell cmdlets to manage my backups and restore using Microsoft 365 Backup?

Yes, you can. Microsoft 365 Backup supports PowerShell cmdlets. You can find the associated PowerShell cmdlets in the [Microsoft 365 Backup Storage Graph APIs](https://learn.microsoft.com/en-us/graph/api/resources/backuprestoreroot) reference guide.

#### How do Microsoft 365 Backup restores interact with site-level and file-level archiving?

Microsoft 365 Archive and Microsoft 365 Backup are orthogonal features. A restore through the Backup tool does not change a SharePoint site’s current site-level tier state. However, when a site is restored to a prior point in time, an individual file’s tier state is restored to the state it had at that point in time.

**Example: Site-level tier state** A site is currently archived, but you restore it to a backup from when it was active. The site remains archived after the restore. Conversely, if the site is currently active, restoring it to a point when it was archived does not archive the site; it remains active.

**Example: File-level tier state** A site is currently active, and a file in it is archived. You restore the site to a point in time when that file was active. After the restore, the file is active. Conversely, if the file is currently active but was archived at the restore point, the restored file is archived.

#### Can I back up every type of SharePoint site?

No, there are some SharePoint sites that are unsupported. While most SharePoint templates are supported, there are a handful of legacy template types which are not. These unsupported templates are:

| Template ID | Template | Template Name |
| --- | --- | --- |
| 70 | SharePoint Embedded container | CSPCONTAINER#0 |
| 6000 | Review Center | REVIEWCTR#0 |
| 3500 | Policy Center | POLICYCTR#0 |
| 16 | Tenant admin site | TENANTADMIN#0 |
| 54 | MySite Host | SPSMSITEHOST#0 |
