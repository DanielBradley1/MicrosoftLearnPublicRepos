<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-reports?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Compliance Reports in Microsoft 365 Backup

Microsoft 365 Backup now provides **compliance reports** to give admins an at-a-glance view of their site/mailbox/onedrive protection status, backup availability aka health, and storage consumption across their tenant. Compliance reports include the following:

- **Item enrollment status** \(Available now\)
- **Restore point availability** \(Coming soon\)
- **Storage consumption insights** \(Coming soon\)

## Item enrollment status

The item enrollment status report gives admins a unified summary of their backup policies so they can quickly confirm that sites, OneDrive accounts, and mailboxes are being protected as expected.

For each workload and policy, admins can view:

- The **item enrollment status %**, calculated as \(number of items in an backed up state ÷ total number of items\) x 100. This includes items that are backed up, removed or paused, actively being deleted, in progress \(adding, removing, or pausing\), and failed.
- The total number of items in a **backed up**, **failed**, or **in-progress** state, each with a link to a detailed view panel. Failed items include error details to help with remediation.
- Detailed policy view, broken down by workload \(SharePoint, OneDrive, and Exchange Online\).

#### How to view the item enrollment status report

1. Sign in to the Microsoft 365 admin center and go to the **Microsoft 365 Backup** overview page.
2. On the **Microsoft 365 Backup** page, select the **Reports** tab \(next to **Backup policies** and **Restorations**\).
3. The **Item enrollment status** tile shows a workload summary, with a progress bar for each workload \(SharePoint, OneDrive, and Exchange\) indicating the percentage of enrolled items that are backed up, in progress, or failed.

   ![Screenshot showing the Overview of the reports](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-report-overview.png?view=o365-worldwide)
4. Select **View more** on the tile to open the detailed **Item enrollment status** page. This page shows:

   - Summary cards for **Backed up**, **In progress**, **Failed**, and **Paused** items, each broken down by workload.
   - **Removed items** and **Items being permanently deleted** counts.


   ![Screenshot showing the detailed report of item enrollment status.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-report-detail-panel.png?view=o365-worldwide)

5. All failed items across every workload are surfaced in a single pane so you don't need to check each workload separately—select the **Failed** card \(or the info icon next to it\) to see the associated error message and take corrective action.
6. Scroll down to the **Backup policies by service** section for the policy-level view. Here you can:

   - Filter by **Policy status** or **Item enrollment** status.
   - Search for a policy by name.
   - Expand each workload \(SharePoint, OneDrive, Exchange\) to drill down further and see each policy's status, included items, and item enrollment count.

Note

The item enrollment status report reflects real-time data.

## Restore point availability \(coming soon\)

This report will help admins confirm that their protected sites, OneDrive accounts, and mailboxes have valid, healthy restore points. Admins will be able to view overall restore point availability as a absolute count across a policy, and drill into individual items to see restore point availability counts \(actual vs. expected\), the latest recovery point, and any missing restore points.

## Storage consumption insights \(coming soon\)

This report will give admins a unified view of billed backup storage consumption for the tenant. Admins will be able to view total backup size by iem, policy and by workload \(SharePoint, OneDrive, and Exchange Online\).

Note

In the meantime, you can check the Azure Cost Management portal as described [here](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide#manage-consumption-and-invoices-for-microsoft-365-backup) for consumption insights.
