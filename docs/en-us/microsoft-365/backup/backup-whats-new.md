<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-whats-new?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-22 -->

# What's new in Microsoft 365 Backup

Use this page to review customer-facing Microsoft 365 Backup changes. **New capabilities** remain new for three months after their customer launch date. When a launch date isn't available, the first public documentation date is used. FAQ updates cover material clarifications. Important notices remain listed while the limitation or administrator action is still relevant.

Developer API changes are tracked separately in [What's new for Microsoft 365 Backup Storage developers](https://learn.microsoft.com/en-us/microsoft-365/backup/storage/backup-3p-whats-new?view=o365-worldwide).

- [New capabilities](#new-capabilities)
- [FAQ updates](#faq-updates)
- [Important notices](#important-notices)

<details>
<summary>**New capabilities** - Launched within the last three months</summary>

## New capabilities

### Configure backup recovery windows

**September 18, 2026**

Backup policies can use recovery windows of 3 months, 6 months, 1 year, or 2 years. Existing policies keep a one-year recovery window unless an administrator changes them.

Note

Shortening a recovery window starts a 30-day grace period before recovery points outside the new window are deleted.

For more information, see [Configure the backup recovery window](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide#configure-the-backup-recovery-window).

### Protect full workloads with exclusions \(preview\)

**September 18, 2026**

Full Workload Backup can automatically protect eligible SharePoint sites, OneDrive accounts, or Exchange mailboxes that aren't assigned to a custom policy. The service checks for newly eligible items every 24 hours, gives custom policies precedence, and supports up to 10,000 exclusions in one operation.

For more information, see [Full Workload Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide#full-workload-backup).

### Expanded backup scale limits

**September 18, 2026**

Microsoft 365 Backup supports up to 1,000,000 items per workload, 100 policies per workload, and 100,000 items per policy. If your organization needs higher scale, contact Microsoft.

For more information, see [Backup scale limits](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview?view=o365-worldwide#backup-scale-limits).

### Set up and migrate pay-as-you-go billing in the Microsoft 365 admin center

**September 3, 2026**

Customers onboarded before April 1, 2026 can use **Migrate** to move Microsoft 365 Backup pay-as-you-go billing management from **Setup** or **Org settings** into the **Billing** experience in the Microsoft 365 admin center. The Azure subscription, resource group, and region are retained, and existing backups aren't disrupted.

For more information, see [Set up pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup?view=o365-worldwide#1-set-up-pay-as-you-go-billing).

### Enable Exchange mailbox billing attribution

**September 3, 2026**

Administrators can consent to include Exchange mailbox identifiers in Azure cost attribution for Microsoft 365 Backup.

Note

`MailboxDbGuid` is an internal identifier and shouldn't be used as a stable external key.

For more information, see [Billing attribution for Exchange mailbox consent](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide#billing-attribution-for-exchange-mailbox-consent).

### Notify multiple administrators about backup events

**September 3, 2026**

Global Administrators and Microsoft 365 Backup Administrators can send daily email digests to as many as 20 recipients, including distribution lists and mail-enabled security groups. Potentially harmful and routine events can be configured separately.

Note

Jobs configured with a 10-minute recovery point objective aren't included. Notifications are sent after the overall policy completes.

For more information, see [Enable email notifications](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup?view=o365-worldwide#enable-email-notifications).

### Browse and restore selected OneDrive and SharePoint content

**September 2, 2026**

Granular restore is generally available. Microsoft 365 Backup administrators can browse or search a protected restore point, select files and folders, and restore them to the original location or a new timestamped folder. In-place restores inherit destination-folder permissions and provide choices for name conflicts.

Note

The SharePoint Backup Admin role is required.

For more information, see [Restore selected content](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-restore-data?view=o365-worldwide#option-2-selected-content-only).

<details>
<summary>**Earlier capability updates from the 12-month review**</summary>

### Attribute OneDrive and SharePoint costs by protection unit

**April 13, 2026**

Azure cost data includes the `protectionunitid` tag for site-level OneDrive and SharePoint cost attribution.

For more information, see [Billing attribution by tenants, service type, and applications](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide#billing-attribution-by-tenants-service-type-and-applications).

### Use additional administrator roles for pay-as-you-go setup

**April 8, 2026**

Billing Administrator and AI Administrator are included among the documented roles for pay-as-you-go setup when the required Azure subscription permissions are also present.

For more information, see [Set up pay-as-you-go billing for Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node).

### Connect multiple billing policies

**March 3, 2026**

Organizations can connect more than one billing policy to Microsoft 365 Backup and divide backup costs among Azure subscriptions.

For more information, see [Set up departmental billing](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide#set-up-departmental-billing).

### Manage backup billing by department

**February 27, 2026**

Departmental billing can associate backup policies with departmental Azure subscriptions and restrict management to administrators with access to the applicable billing policy.

For more information, see [Manage consumption and invoices for Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide).

### Use Microsoft 365 Backup in GCC

**February 23, 2026**

Microsoft 365 Backup is available for Government Community Cloud organizations.

For more information, see [Overview of Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview?view=o365-worldwide).

### Use the pay-as-you-go Billing experience

**January 5, 2026**

New customers can set up Microsoft 365 Backup pay-as-you-go billing from the **Billing** node in the Microsoft 365 admin center.

For more information, see [Set up pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup?view=o365-worldwide#1-set-up-pay-as-you-go-billing).

### Offboard individual protection units in the UI or with workload-specific commands

**October 23, 2025**

Administrators can permanently delete backups for selected sites, mailboxes, or users from **Removed Items** and can undo the request during the grace period. Automation can use the workload-specific Microsoft 365 Backup Storage commands.

For more information, see [Offboard specific sites, mailboxes, or users](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-offboarding?view=o365-worldwide#offboard-specific-sites-mailboxes-or-users).
</details>
</details>

<details>
<summary>**FAQ updates** - New or materially revised customer guidance</summary>

## FAQ updates

### How should restore performance estimates be interpreted?

**September 18, 2026**

Performance figures are median expectations. OneDrive and SharePoint estimates emphasize express restore points and cumulative throughput of roughly 6,000 sites and accounts per day. Exchange restores typically process about 100 to 500 items per mailbox per minute. Performance tends to fall below the median when item counts exceed fleet medians and can be better for smaller item counts.

For more information, see [Restoration performance](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview?view=o365-worldwide#restoration-performance).

### What content isn't supported by granular restore?

**September 2, 2026**

SharePoint granular restore doesn't support content in Information Rights Management-enabled document libraries or locked SharePoint sites.

For more information, see [Considerations when using restore](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-restore-data?view=o365-worldwide#considerations-when-using-restore).

### How do I recover a permanently inactive mailbox?

**September 2, 2026**

Use **Recover an inactive mailbox**. **Restore an inactive mailbox** doesn't preserve the backup data from the old mailbox.

For more information, see [Considerations when using restore](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-restore-data?view=o365-worldwide#considerations-when-using-restore).

### What should I do when ExternalDirectoryObjectID still exists?

**March 20, 2026**

The user was deleted less than 30 days ago and remains soft deleted. Restore the user in the Microsoft 365 admin center before continuing the backup restore flow.

For more information, see [Restore a deleted user's OneDrive account or Exchange mailbox](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-faq?view=o365-worldwide#how-can-i-restore-the-onedrive-account-or-exchange-mailbox-for-a-user-who-is-deleted-from-microsoft-entra-id-formerly-azure-active-directory).

### How can I narrow an Exchange granular restore?

**February 4, 2026**

Search can be filtered by time range, sender, recipient, attachment, subject, and content type. Each restore is limited to 1,000 items, so broad searches need to be refined.

For more information, see [Restore data in Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-restore-data?view=o365-worldwide).

### Which Exchange recipient types aren't supported?

**January 28, 2026**

Group mailboxes and room mailboxes can't be added to a Microsoft 365 Backup policy.

For more information, see [Create Exchange backup policies](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide).
</details>

<details>
<summary>**Important notices** - Active limitations and administrator actions</summary>

## Important notices

### Review a shorter recovery window before the grace period ends

**September 18, 2026**

Decreasing a recovery window is destructive. Recovery points older than the new window are deleted after a 30-day grace period.

For more information, see [Configure the backup recovery window](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide#configure-the-backup-recovery-window).

### Don't treat MailboxDbGuid as a stable external identifier

**September 3, 2026**

The `MailboxDbGuid` tag used in Azure consumption reporting is intended for Microsoft internal use, and its value might change.

For more information, see [Billing attribution for Exchange mailbox consent](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide#billing-attribution-for-exchange-mailbox-consent).

### Hybrid Exchange deployments aren't supported

**January 24, 2026**

Only mailboxes fully hosted in Exchange Online can be protected by Microsoft 365 Backup.

For more information, see [Create Exchange backup policies](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide).

### Billing setup paths differ for new and existing customers

**January 23, 2026**

New customers use the **Billing** experience. Customers whose billing remains under **Setup** or **Org settings** can view, edit, or migrate their existing pay-as-you-go configuration from the Microsoft 365 admin center.

For more information, see [Set up pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup?view=o365-worldwide#1-set-up-pay-as-you-go-billing).

### Some SharePoint site templates can't be protected

**December 4, 2025**

Unsupported templates include SharePoint Embedded containers, Review Center, Policy Center, tenant admin sites, and MySite Host.

For more information, see [Can I back up every type of SharePoint site?](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-faq?view=o365-worldwide#can-i-back-up-every-type-of-sharepoint-site).

### Turning off pay-as-you-go begins offboarding

**November 25, 2025**

To disconnect Microsoft 365 Backup billing, turn off Backup from the pay-as-you-go settings. Disabling the tool starts the offboarding process for policies and backed-up data.

For more information, see [Offboarding in Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-offboarding?view=o365-worldwide).
</details>
