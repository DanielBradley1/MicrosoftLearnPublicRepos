<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-offboarding?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Offboarding in Microsoft 365 Backup

To stop using the Microsoft 365 Backup tool, you must offboard usage. This action includes pausing and deleting all active policies and deleting all of the backed-up data. You can initiate offboarding in two ways:

- Disable the tool in the pay-as-you-go billing setup panel where you first enabled the tool.
- If your billing account goes into an unhealthy state.

## Offboard specific sites, mailboxes, or users

To comply with GDPR regulations, delete backups of specific sites, mailboxes, or users by using the offboarding feature.

Note

To offboard a site, mailbox, or user, first remove it from the policy. Remove the item from the policy before proceeding with offboarding.

Follow these steps to offboard a site, mailbox, or user:

1. Go to the **Removed Items** tab and find the site, mailbox, or user that you want to offboard.
2. Select the item, and then choose **Delete Sites Backup** or **Delete Backup**, depending on the item type.  ![Screenshot of a offboarding option](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-option.png?view=o365-worldwide)
3. When the confirmation dialog appears, read the information and warnings carefully. Enter your email address in the confirmation field to verify the deletion request.  ![Screenshot of a confirmation option](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-confirmation.png?view=o365-worldwide)
4. Confirm the action to proceed.
5. After you submit the deletion request, the item moves from the **Removed Items** tab to the **Items Being Permanently Deleted** tab.  ![Screenshot of a overview page of offboarding](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-overview.png?view=o365-worldwide)
6. Monitor the progress of the offboarding process in the **Items Being Permanently Deleted** tab. When the process finishes, the backup is permanently deleted from Microsoft 365 Backup.

Note

From the **Items being permanently deleted** view, you can also request a faster deletion that shortens the grace period for selected items to seven days. A faster deletion requires approval from a second admin. For more information, see [Backup critical action approval](#backup-critical-action-approval).

To cancel offboarding during the grace period:

If you need to cancel the offboarding request during the grace period, follow these steps:

1. Go to the **Items Being Permanently Deleted** tab.
2. Select the site, mailbox, or user that you want to cancel offboarding for.
3. Choose the **Undo Deletion** option.  ![Screenshot of cancel offboarding](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-cancel-offboarding.png?view=o365-worldwide)
4. Confirm the action when prompted.  ![Screenshot of cancel offboarding confirmation](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-cancel-offboarding-confirmation.png?view=o365-worldwide)
5. The offboarding process is canceled. The selected item moves back to the **Removed Items** tab and remains in its previous removed state.

## Offboarding recovery undo period

If offboarding from Microsoft 365 Backup starts because of either an explicit request from you or an unhealthy billing state, the grace periods shown in the following table start.

![Screenshot of a data table showing the offboarding undo periods.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-offboarding-time.png?view=o365-worldwide)

If you bring your billing back to a healthy state or ask support to reverse the offboarding, you can use the tool again and you don't lose any backups.

Tip

If you need to permanently delete specific offboarded items sooner, you can shorten their grace period to seven days. Because shortening a grace period accelerates permanent deletion, this action requires approval from a second admin. For more information, see [Backup critical action approval](#backup-critical-action-approval).

## Backup critical action approval

Some actions against your backup data are hard to reverse. Shortening the offboarding grace period for an item accelerates the permanent deletion of its backup. **Backup critical action approval** protects actions like this with a two-person rule: a critical action can't proceed until at least two independent approvers approve the specific request. The approval is required for the request in front of the approvers and applies only to the items in that request.

In this release, **Backup critical action approval** gates one action: shortening the offboarding grace period for specific items from 90 days to seven days. An admin requests the shorter grace period for items that are already in the offboarding grace window, and the reduction applies only after the request reaches approval quorum.

### How approval works

- **Approver roster.** Your tenant keeps a roster of at least two approvers who hold the approval privilege. You can't request a critical action until you set up the roster.
- **Quorum of two.** Each request needs two approvals from aged approvers. When exactly two approvers are configured, the requestor's own approval counts toward quorum. When three or more approvers are configured, the requestor is excluded and two other approvers must approve.
- **Aging window.** A newly nominated approver must wait through a fixed two-day aging window before they can approve. The aging window gives you time to notice an approver account that you didn't authorize.
- **Request lifetime.** A request stays open for 30 days. If it doesn't reach quorum in that time, it expires and no data changes. The requestor can cancel a request at any time while it's pending.
- **Fail-safe default.** While fewer than two aged approvers are configured, the tenant stays at the 90-day grace period and new faster-deletion requests are blocked.

Note

The two-day aging window, the 30-day request lifetime, and the two-approver quorum are fixed and aren't configurable per tenant.

### Eligible roles

An approver must hold one of the following roles. Only a **Global Admin** or **Backup Admin** can manage the roster by nominating or removing approvers. Approvers who hold the other roles can approve or decline requests but can't change the roster.

- **Global Admin**
- **Backup Admin**
- **SharePoint Admin**
- **Exchange Admin**
- **SharePoint Backup Admin**
- **Exchange Backup Admin**

### Set up the approver roster

You can set up the roster as a Global Admin or Backup Admin. An admin can't add themselves as an approver.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home).
2. Select **Settings**, and then select **Microsoft 365 Backup** from the list of products.
3. On the **Microsoft 365 Backup** page, select **Settings**, and then select **Backup critical action approval**.
4. Select **Nominate approvers**, select at least two eligible admins, and then confirm. Each nominee becomes an approver immediately and is notified.
5. Wait for the 2-day aging window to pass for the second approver. When at least two approvers have aged in, the roster is armed and a setup-complete confirmation appears.

Note

Removing and re-adding an approver restarts their 2-day aging window. You can't remove approvers below the floor of two. If an approver loses their eligible role, they're removed automatically. This change can drop the roster below two and return the tenant to the 90-day grace period until you add another approver.

### Request a faster deletion

Any eligible admin can request a faster deletion. The request applies only to items that are currently in the offboarding grace window.

1. On the **Microsoft 365 Backup** page, select the **Items being permanently deleted** metric to open the deletion panel.
2. Select one or more items that have the **Delete initiated** status. Items are organized by workload under the SharePoint, OneDrive, and Exchange subtabs.
3. Select **Shorten grace period to 7 days**. This option is unavailable when fewer than two aged approvers are configured, and an info banner links you to the roster setup.
4. In the confirmation dialog, review the warning that this action accelerates permanent deletion, enter your sign-in email to confirm, and submit the request.
5. The selected items move to a pending-approval status while the request waits for approval quorum.

### Review and approve or decline a request

An aged approver can approve a request. Review the items, the approvals received so far, and the request timeline before you act. Each approver can act once, and the action is final.

1. On the **Microsoft 365 Backup** page, select **Settings**, and then select **Backup critical action approval**.
2. Under **Approval requests**, select **Review & approve** for the request you want to act on.
3. Review the request details, including the items in the request, who requested it, the approvals received, and the timeline. To download the item list, select **Export list**.
4. To approve, select **Approve reduction**. This control is styled as a destructive action. When the second approval is recorded, the 7-day deletion schedule applies immediately to the valid items in the request.
5. To decline, select **Decline**. Declining is a personal opt-out and doesn't close the request. Other approvers, including any added later, can still approve before the request expires.

### Undo a shortened grace period

Restoring an item to its original 90-day grace period is a safe direction, so it doesn't require approval. Any admin can restore an affected item to the 90-day grace period at any time before the item is permanently deleted. After an item is purged, the deletion can't be undone.
