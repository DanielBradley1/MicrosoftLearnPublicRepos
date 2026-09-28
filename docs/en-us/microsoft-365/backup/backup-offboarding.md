<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-offboarding?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Offboarding in Microsoft 365 Backup

To no longer use the Microsoft 365 Backup tool, you must offboard usage. This action includes pausing and deleting all active policies and deleting all of the backed-up data. There are two ways that offboarding is initiated:

- Disable the tool in the pay-as-you-go billing setup panel where you first enabled the tool.
- If your billing account goes into an unhealthy state.

## Offboarding specific sites, mailboxes, or users

If you want to delete backups of specific sites, mailboxes, or users to comply with GDPR regulations, you can do so using the offboarding feature.

Note

For you to be able to offboard a site, mailbox, or user, it should be removed from policy first. You kindly remove it from a policy before proceeding with offboarding.

Here's the steps you can follow to offboard a site/mailbox/user:

1. Navigate to the Removed Items tab and locate the site, mailbox, or user that you want to offboard.
2. Select the item, then choose Delete Sites Backup \(or the equivalent Delete Backup option, depending on the item type\).  ![Screenshot of a offboarding option](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-option.png?view=o365-worldwide)
3. A confirmation dialog will appear. Carefully read the information and warnings displayed. Enter your email address in the confirmation field to verify the deletion request.  ![Screenshot of a confirmation option](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-confirmation.png?view=o365-worldwide)
4. Confirm the action to proceed.
5. After the deletion request is submitted, the item will move from the Removed Items tab to the Items Being Permanently Deleted tab.  ![Screenshot of a overview page of offboarding](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-overview.png?view=o365-worldwide)
6. Monitor the progress of the offboarding process in the Items Being Permanently Deleted tab. Once the process is complete, the backup will be permanently deleted from Microsoft 365 Backup.

To cancel offboarding within the grace period:

If you need to cancel the offboarding request within the grace period, follow these steps:

1. Navigate to the Items Being Permanently Deleted tab.
2. Select the site, mailbox, or user that you want to cancel offboarding.
3. Choose the Undo Deletion option.  ![Screenshot of cancel offboarding](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-cancel-offboarding.png?view=o365-worldwide)
4. Confirm the action when prompted.  ![Screenshot of cancel offboarding confirmation](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-cancel-offboarding-confirmation.png?view=o365-worldwide)
5. The offboarding process will be canceled, and the selected item will be moved back to the Removed Items tab, where it will remain in its previous removed state.

## Offboarding recovery undo period

If offboarding from Microsoft 365 Backup is begun due to either an explicit request from you or due to an unhealthy billing state, the grace periods shown in the following table initiate.

![Screenshot of a data table showing the offboarding undo periods.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-time.png?view=o365-worldwide)

By bringing your billing back to a healthy state or by asking support to reverse the offboarding, the tool becomes usable again and no backups are lost.
