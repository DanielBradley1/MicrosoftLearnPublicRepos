<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# Create, view, and edit backup policies in Microsoft 365 Backup

## Create backup policies

To use Microsoft 365 Backup for SharePoint, Exchange, or OneDrive, you need to create a backup policy for each product. A *policy* represents the backup plan defined by admins for protecting the Microsoft 365 data of an organization.

A policy contains details of what data \(SharePoint sites, Exchange mailboxes, and OneDrive accounts\) to protect. You can set the **Recovery window** when you create a policy and change it later on an active policy. The backup frequency isn't currently variable or modifiable. For more information, see [Configure the backup recovery window](#configure-the-backup-recovery-window).

You can create more than one backup policy for each product \(SharePoint, Exchange, and OneDrive\) with a limit of 100 policies per product, and each backup policy can protect up to 100,000 items. This allows you to segregate your data by logical partitions such as department, geography, and so on for ease of management and administration. Note that any SharePoint site, Exchange mailbox, or OneDrive account can be part of one backup policy only. For more information about capacity limits, see [Backup scale limits](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview?view=o365-worldwide#backup-scale-limits).

Tip

You can enable Full Workload Backup to automatically protect all eligible items in the selected workload that aren't already included in other backup policies. For more information, see [Full Workload Backup](#full-workload-backup).

Note

You can also use PowerShell cmdlets to perform these operations by following these steps:

1. Go to the [Microsoft 365 Backup Storage Graph APIs](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangeprotectionpolicies) documentation for the specific action you want to perform-for example, creating a SharePoint policy.
2. Scroll to the **Example request** section and select the **PowerShell** tab.
3. Install the Microsoft.Graph.BackupRestore module as shown in the example.
4. Run the provided PowerShell command in an Admin PowerShell session to execute the desired action.

  


<iframe src="https://learn-video.azurefd.net/vod/player?id=2cdeb3f7-2565-414c-9afe-e2deb5dc77c2" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

  


Select the **SharePoint**, **Exchange**, or **OneDrive** tab for steps to create a backup policy for that product.

- [SharePoint](#tabpanel_1_sharepoint)
- [Exchange](#tabpanel_1_exchange)
- [OneDrive](#tabpanel_1_onedrive)

Follow these steps to set up a backup policy for SharePoint sites using Microsoft 365 Backup.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home).
2. Select **Settings**.
3. Select **Microsoft 365 Backup** from the list of products.
4. On the **Microsoft 365 Backup** page, in the **SharePoint** section, select **Set up policy**.

   ![Screenshot of the Microsoft 365 Backup page with SharePoint highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-setup-backup-page-sharepoint.png?view=o365-worldwide)
5. On the **Overview** page, review the backup features for SharePoint, and then select **Next**.

   ![Screenshot of the Overview page for SharePoint.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-overview-page-sharepoint.png?view=o365-worldwide)
6. On the **Choose selection method** page, you can set up SharePoint sites using any of the available methods. A protection scope is the scope of SharePoint sites that you want to protect with Microsoft 365 Backup.

   ![Select user accounts](https://learn.microsoft.com/en-us/microsoft-365/backup/media/backup-view-edit-policies/select-user-accounts.png?view=o365-worldwide)


   a. Under **Upload a list of sites in a CSV file**, you can upload a list of accounts to back up via a CSV file.


   The CSV upload feature for bulk addition of sites or user accounts in the backup policy creation workflow can accommodate a maximum of 50,000 entries per CSV file.


   b. Under **Back up sites that match specific filters**, you can select **Site name or URL contains** or **Site last modified**, or both.


   The rule-based feature for bulk addition of sites in the backup policy creation workflow allows you to add up to 10 site names or URLs at a time. Each keyword can have a minimum of three characters and maximum of 255 characters.


   Note


   The site filters are in preview.


   c. Under **Select sites individually**, you can search and select sites you want to add to a backup policy.


   Note


   Some legacy SharePoint site templates are not supported by Microsoft 365 Backup. Please view the [FAQ page](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-faq) to learn more.


   d. Under **Back up all SharePoint sites**, you can create the [full workload backup](#full-workload-backup) policy for SharePoint to automatically protect all SharePoint sites not already included in other backup policies.


   Note


   The full workload backup feature is in preview.

7. Select **Next** to move to the **Backup Settings** page, where you can provide a name for your policy.
8. On the **Review SharePoint backup policy** page, review the information to make sure it's how you want it, and then select **Create policy** \(or **Update policy** if it's an update\).

   ![Screenshot of the Review SharePoint backup policy page.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-review-policy-sharepoint.png?view=o365-worldwide)
9. The backup policy for SharePoint is created.

   ![Screenshot of the SharePoint backup policy created page.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-created-sharepoint.png?view=o365-worldwide)

   Once the sites are added to a backup policy, it might take up to 15 minutes per 1,000 sites for restore points to become available for restore.

Follow these steps to set up a backup policy for Exchange mailboxes sites using Microsoft 365 Backup.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home).
2. Select **Settings**.
3. Select **Microsoft 365 Backup** from the list of products.
4. On the **Microsoft 365 Backup** page, in the **Exchange** section, select **Set up policy**.

   ![Screenshot of the Microsoft 365 Backup page with Exchange highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-setup-backup-page-exchange.png?view=o365-worldwide)
5. On the **Overview** page, review the backup policy attributes for Exchange, and then select **Next**.

   ![Screenshot of the Overview page for Exchange.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-overview-page-exchange.png?view=o365-worldwide)
6. On the **Choose selection method** page, you can select shared or user mailboxes using any of the available methods. Other Exchange recipient types, such as room and group mailboxes, are not supported at this time. A protection scope is the scope of mailboxes within Exchange that you want to protect with Microsoft 365 Backup.

   a. Under **Upload a list of mailboxes in a CSV file**, you can upload a list of accounts to back up via a CSV file.

   The CSV upload feature for bulk addition of mailboxes in the backup policy creation workflow can accommodate a maximum of 50,000 entries per CSV file.

   b. Under **Using a dynamic rule**, you can select **Distribution lists** or **Security groups**, or both. With dynamic rules, any changes to membership in the selected distribution lists and security groups are automatically reevaluated daily, ensuring the backup policy reflects those membership changes regularly.

   For example, if a user is added to a distribution list included in the dynamic rule, that user is included in the backup policy within a day. After that, Microsoft 365 Backup will create restore points for that user. If a user that was previously in the included distribution list is removed from that list, then they're removed from the backup policy within 24 hours. The user's existing backups remain restorable until they expire based on their recovery window. However, new backups aren't taken until the user is re-added to the included distribution list or manually re-added through a static addition.

   Note

   The dynamic rule feature is in preview.

   c. Under **Using filters**, you can select **Distribution lists** or **Security groups**, or both. The distribution list and security group are flattened when added, meaning the policy doesn't update dynamically if the groups or distribution list are updated later.

   Note

   Members of security groups that are shared mailboxes are currently not added. You'll need to add shared mailboxes manually.
7. Select **Next** to move to the **Backup Settings** page, where you can provide a name for your policy.
8. On the **Review Exchange backup policy** page, review the information to make sure it's how you want it, and then select **Create policy** \(or **Update policy** if it's an update\).
9. The backup policy for Exchange is created.

   ![Screenshot of the Exchange backup policy created page.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-created-exchange.png?view=o365-worldwide)

   Once the mailboxes are added to a backup policy, it might take up to 15 minutes per 1,000 mailboxes for restore points to become available for restore.

Follow these steps to set up a backup policy for OneDrive accounts using Microsoft 365 Backup.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home).
2. Select **Settings**.
3. Select **Microsoft 365 Backup** from the list of products.
4. On the **Microsoft 365 Backup** page, in the **OneDrive** section, select **Set up policy**.

   ![Screenshot of the Microsoft 365 Backup page with OneDrive highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-setup-backup-page-onedrive.png?view=o365-worldwide)
5. On the **Overview** page, review the backup policy attributes for OneDrive, and then select **Next**.

   ![Screenshot of the Overview page for OneDrive.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-overview-page-onedrive.png?view=o365-worldwide)
6. On the **Choose selection method** page, you can select OneDrive user accounts using any of the available methods. A protection scope is the scope of user accounts within OneDrive that you want to protect with Microsoft 365 Backup.

   ![Select user accounts odb](https://learn.microsoft.com/en-us/microsoft-365/backup/media/backup-view-edit-policies/select-user-accounts-odb.png?view=o365-worldwide)


   a. Under **Upload a list of accounts in a CSV file**, you can upload a list of accounts to back up via a CSV file.


   The CSV upload feature for bulk addition of sites or user accounts in the backup policy creation workflow can accommodate a maximum of 50,000 entries per CSV file.


   b. Under **Using a dynamic rule**, you can select **Distribution lists** or **Security groups**, or both. With dynamic rules, any changes to membership in the selected distribution lists and security groups are automatically reevaluated daily, ensuring the backup policy reflects those membership changes regularly.


   For example, if a user is added to a distribution list included in the dynamic rule, that user is included in the backup policy within a day. After that, Microsoft 365 Backup will create restore points for that user. If a user that was previously in the included distribution list is removed from that list, then they're removed from the backup policy within 24 hours. The user's existing backups remain restorable until they expire based on their recovery window. However, new backups aren't taken until the user is re-added to the included distribution list or manually re-added through a static addition.


   Note


   The dynamic rule feature is in preview.


   c. Under **Using filters**, you can select **Distribution lists** or **Security groups**, or both. The distribution list and security group are flattened when added, meaning the policy doesn't update dynamically if the groups or distribution list members are updated later.


   The rule-based feature for bulk addition of user accounts via security groups or distribution lists can accommodate a maximum of three groups at a time. These rules are static and applied one time only. That is, the security groups or distribution lists are flattened at the time of adding to the backup configuration policy. For example, groups or lists aren't dynamically updated in the system if users are added or removed from the original security group.


   d. Under **Select accounts individually**, you can search and select accounts you want to add to a backup policy.


   e. Under **Back up all OneDrive accounts**, you can create the [full workload backup](#full-workload-backup) policy for OneDrive to automatically protect all OneDrive accounts not already included in other backup policies.


   Note


   The full workload backup feature is in preview.

7. Select **Next** to move to the **Backup Settings** page, where you can provide a name for your policy.
8. On the **Review OneDrive backup policy** page, review the information to make sure it's how you want it, and then select **Create policy** \(or **Update policy** if it's an update\).
9. The backup policy for OneDrive is created.

   ![Screenshot of the OneDrive backup policy created page.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-created-onedrive.png?view=o365-worldwide)

   Once the sites are added to a backup policy, it might take 15 to 25 minutes per 1,000 sites for restore points to become available for restore.

## Configure the backup recovery window

The **Recovery window** determines how long Microsoft 365 Backup keeps recovery points for the artifacts in a backup policy. You set the recovery window on a policy, and it applies to every artifact in that policy. Existing policies and artifacts default to a 1-year recovery window.

You can set the recovery window to one of the following values:

- 3 months
- 6 months
- 1 year
- 2 years

1. In the create-policy wizard, on the **Backup Settings** page, set the **Recovery window** for the policy.
2. Review your choice on the **Review** page, and then select **Create policy**.
3. To change the recovery window later, open an active policy, update the **Recovery window**, and then select **Update policy**.

You can change the recovery window on an active policy. You can't change it on a policy that is paused or has a run in progress.

Increasing the recovery window applies immediately. Decreasing the recovery window is a destructive action, because recovery points older than the new window are deleted. A reduction can happen in two ways: you decrease the recovery window on a policy, or you move an artifact into a policy that has a shorter recovery window. In either case, to protect against accidental or malicious reductions, the deletion takes effect only after a 30-day grace period, giving an admin time to review and, if needed, act before any recovery points are removed.

When you remove an artifact from a policy, it keeps the last recovery window that applied to it and appears in the **Removed items** list until that window ends.

## View and edit backup policies

You can edit the scope of OneDrive accounts, SharePoint sites, and Exchange mailboxes associated with a backup policy. As part of edit, you can either add new accounts, sites, or mailboxes to or remove them from backup. Removing accounts, sites, and mailboxes from Microsoft 365 Backup doesn't mean existing backups aren't deleted, rather it means additional backups aren't taken.

Select the **SharePoint**, **Exchange**, or **OneDrive** tab for steps to view and edit backup policies for that product.

- [SharePoint](#tabpanel_2_sharepoint)
- [Exchange](#tabpanel_2_exchange)
- [OneDrive](#tabpanel_2_onedrive)

Follow these steps to view and edit backup policies in SharePoint.

1. In the Microsoft 365 admin center, on the **Microsoft 365 Backup** page, select the **Backup policies** tab to view the list of all backup policies created in your organization. You can filter the list of policies by SharePoint **Service** to view the list of all SharePoint backup policies created in your organization. To edit any specific policy, select that policy and then select **View details.**

   ![Screenshot showing the view and edit backup policy for SharePoint in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-sharepoint.png?view=o365-worldwide)
2. On the policy specific panel, on the **Policy details** tab, in the **Scope** area, select **Edit**.
3. You can either add new sites to or remove sites from an existing SharePoint backup policy.

   a. To add new sites, on the **Included sites** tab, select **+ Add sites**.

   b. Select sites by any method as discussed in the creation section. Once you add sites to the list, follow the prompts to update the policy.

   ![Screenshot showing how to add sites to the existing SharePoint backup policy in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-sharepoint-add-site.png?view=o365-worldwide)

   c. To remove sites from existing SharePoint backup policy, on the **Included sites** tab, select the relevant sites, and then select **Remove**. Once you're done with your changes, follow the prompts to remove the sites. The removed sites are moved to the **Removed Items** tab under the **Backup policies** tab.

   ![Screenshot showing how to remove sites from SharePoint backup policy in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-remove-site.png?view=o365-worldwide)
4. Once you make your changes, follow the prompts to update the policy.

   ![Screenshot of the updated SharePoint sites backup policy panel in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-updated-sites.png?view=o365-worldwide)

   Note

   Removing sites from backup policy means no future backups are taken for those removed sites. Existing backups for the removed sites aren't deleted and will be charged.

Follow these steps to view and edit backup policies for Exchange.

1. In the Microsoft 365 admin center, on the **Microsoft 365 Backup** page, select the **Backup policies** tab to view the list of all backup policies created in your organization. You can filter the list of policies by Exchange **Service** to view the list of all Exchange Online backup policies created in your organization. To edit any specific policy, select that policy and then select **View details**.

2. You can either add new mailboxes to or remove mailboxes from the existing Exchange backup policy.

   a. To add new shared or user mailboxes, use the following method:

   - On the policy specific panel, on the **Policy details** tab, in the **Scope** area, select **Edit**.
   - To add new mailboxes, on the **Included sites** tab, select **+ Add mailboxes**.
   - Select the mailboxes by using any of the four available methods as discussed in the creation section. Once you add mailboxes to the list, follow the prompts to update the policy.


   ![Screenshot showing how to add mailboxes to the existing Exchange backup policy in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-exchange-add-mailbox.png?view=o365-worldwide)


   b. To remove user mailboxes from existing backup policy, on the **Included mailboxes** tab, select the user mailboxes from the list, and select **Remove**.


   Mailboxes added to a backup policy through a dynamic rule can't be individually removed. To exclude these mailboxes from the backup policy, you must modify the rule conditions. For example, if User A is part of Distribution List P, removing User A from the list excludes them from the policy. Alternatively, removing the entire distribution list from the rule removes all mailboxes that were added through that list from the backup policy.


   ![Screenshot showing how to remove user mailboxes from Exchange backup policy in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-remove-mailbox.png?view=o365-worldwide)

3. The removed mailboxes are moved to the **Removed Items** tab under the **Backup policies** tab.

   ![Screenshot of the updated Exchange mailbox backup policy panel in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-updated-mailbox.png?view=o365-worldwide)

   Note

   Removing mailboxes from backup policy means no future backups are taken for those removed mailboxes. Existing backups for those mailboxes aren't deleted and will be charged.

Follow these steps to view and edit backup policies for OneDrive.

1. In the Microsoft 365 admin center, on the **Microsoft 365 Backup** page, select the **Backup policies** tab to view the list of all backup policies created in your organization. You can filter the list of policies by OneDrive **Service** to view the list of all OneDrive backup policies created in your organization. To edit any specific policy, select that policy and then select **View details**.

2. You can either add new accounts to or remove accounts from an existing OneDrive backup policy.

   a. To add new accounts, use the following method:

   - On the policy specific panel, on the **Policy details** tab, in the **Scope** area, select **Edit**.
   - To add new accounts, on the **Included accounts** tab, select **+ Add accounts**.
   - Select the accounts by using any of the four available methods as discussed in the creation section. Once you add accounts to the list, follow the prompts to update the policy.


   ![Screenshot showing how to add user accounts to the existing OneDrive backup policy in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-add-account.png?view=o365-worldwide)


   b. To remove accounts from existing backup policy, on the **Included accounts** tab, select the accounts from the list, and then select **Remove**. Once you make your changes, follow the prompts to remove the accounts.


   Accounts added to a backup policy through a dynamic rule can't be individually removed. To exclude these accounts from the backup policy, you must modify the rule conditions. For example, if User A is part of Distribution List P, removing User A from the list excludes them from the policy. Alternatively, removing the entire distribution list from the rule removes all accounts that were added through that list from the backup policy.


   ![Screenshot showing how to remove user accounts from OneDrive backup policy in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-remove-account.png?view=o365-worldwide)

3. The removed accounts are moved to the **Removed Items** tab under the **Backup policies** tab.

   ![Screenshot of the updated OneDrive accounts backup policy panel in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-policy-updated-account.png?view=o365-worldwide)

   Note

   Removing accounts from backup policy means no future backups are taken for those removed accounts. Existing backups for those accounts aren't deleted and will be charged.

## Rename a policy

- To rename an existing policy, on the **Backup policies** tab, select the specific policy from the list of policies.
- Select **Rename.** This opens up a new panel where you can specify the new policy name.
- Note that policy name can have a maximum of 20 characters only and policy names must be unique.
- Select **Rename** and the new policy name takes effect instantly.

## Full Workload Backup

Full Workload Backup provides automatic protection for all eligible SharePoint sites, OneDrive accounts, or Exchange mailboxes in your organization that aren't already protected by another backup policy. It helps ensure comprehensive workload protection without requiring you to manually maintain backup policies as new protection units are created.

You can enable Full Workload Backup independently for SharePoint, OneDrive, and Exchange. When enabled, Microsoft 365 Backup creates a Full Workload Backup policy for the selected workload. Other “custom” backup policies continue to work without changes, and any new protection units are automatically protected. You can also maintain an exclusion list to keep specific protection units out of Full Workload Backup protection.

Note

The full workload backup feature is in preview.

### How Full Workload Backup works

Full Workload Backup works alongside your custom backup policies to provide comprehensive protection for an entire workload.

- **Protection scope** – Full Workload Backup automatically protects all eligible protection units that aren't already included in a custom backup policy, added to the exclusion list, or in the process of being permanently deleted from Microsoft 365 Backup.
- **Policy precedence** – Custom backup policies always take precedence over Full Workload Backup. A protection unit that's already included in a custom backup policy \(in an active or paused state\) will not be protected by the Full Workload Backup policy. If you attempt to add a protection unit that is already protected by Full Workload Backup to a custom backup policy, the protection unit will be moved to that custom policy automatically, with no gap in its recovery point coverage.
- **Automatic protection of new protection units** – Microsoft 365 Backup checks for newly created SharePoint sites, OneDrive accounts, and Exchange mailboxes every 24 hours.

### Enable Full Workload Backup

The setup experience is the same for SharePoint, OneDrive, and Exchange. The following example uses SharePoint.

1. On **Microsoft 365 Backup** dashboard, select **Back up sites**, and then choose **All sites**. Alternatively, on the **Choose selection method** step, select **Back up all SharePoint sites**. ![Day 0 \_ Backup policies](https://learn.microsoft.com/en-us/microsoft-365/backup/media/backup-view-edit-policies/day-0---backup-policies.png?view=o365-worldwide)
2. On the **Overview page**, review the information about the Full Workload Backup policy, and then select the checkbox to continue.
3. On the **Exclude sites** page, select **No** if you want to protect all SharePoint sites. If you want to exclude specific sites from protection, continue to the next step.
4. \(Optional\) Upload a CSV file to exclude specific sites from Full Workload Backup protection. ![Exclusion while policy creation](https://learn.microsoft.com/en-us/microsoft-365/backup/media/backup-view-edit-policies/exclusion-while-policy-creation.png?view=o365-worldwide)
5. On the **Review and finish** page, review the configuration, and then select **Next** to create the **Full SharePoint Backup** policy.

### Exclusion List

The exclusion list allows you to exclude specific protection units from Full Workload Backup protection. This is useful when you don't want certain sites, accounts, or mailboxes to be protected by the Full Workload Backup policy.

The exclusion list applies only to the Full Workload Backup policy. Protection units added to the exclusion list can still be protected through a custom backup policy without restriction.

You can exclude up to 10,000 protection units in a single operation.

When you remove a protection unit from the exclusion list, it returns to the Full Workload Backup protection scope and is automatically protected by the Full Workload Backup policy.

#### Manage the exclusion List

1. On **Microsoft 365 Backup** page, select **Backup policies** tab.

2. Select the **Full Workload Backup** policy for the workload, and then select **View details**.

3. Open the **Excluded** tab.

4. Select **Exclude more**. ![Exclude more sites](https://learn.microsoft.com/en-us/microsoft-365/backup/media/backup-view-edit-policies/exclude-more-sites.png?view=o365-worldwide)

5. Upload a CSV file containing the protection units that you want to exclude.

6. Select **Save**.

### Removal of protection units from backup policies

After you enable Full Workload Backup, removing protection units from backup policies works as follows.

**Remove a protection unit from a custom backup policy**

When Full Workload Backup is active and you remove a protection unit from a custom backup policy, choose one of the following options:

- **Add to exclusion list** – With this action, the protection unit will be prevented from automatically moving into the Full Workload Backup. Choose this option if you do not want new backups to be taken for the protection unit removed from the custom backup policy. Regardless, existing backups for that protection unit will remain for its defined retention period.
- **Move to Full Workload Backup** – The protection unit is removed from the custom backup policy and added to the Full Workload Backup policy in its next run.

**Remove a protection unit from the Full Workload Backup policy**

When you remove a protection unit from the Full Workload Backup policy, it's added to the policy's exclusion list. This keeps Full Workload Backup from automatically re-protecting it again, and no new backups are taken for it. Your existing backups stay available for restore based on your retention settings, and you can add the protection unit to any other backup policy.

### Turn off Full Workload Backup

1. On the **Backup policies** page, select the **Full Workload Backup** policy for the workload.
2. Select **Turn off Full Workload Backup** either from the command bar or the policy details pane.

   ![disable full workload backup](https://learn.microsoft.com/en-us/microsoft-365/backup/media/backup-view-edit-policies/disable-full-workload-backup.png?view=o365-worldwide)

3. Review the information on the confirmation page, and then select **Confirm**.

   After Full Workload Backup is turned off:

   - The Full Workload Backup policy is removed.
   - Protection units associated only with the Full Workload Backup policy move to the **Removed items** tab. As a result, for the protection units listed in that tab,

     - Existing backups stay available for restore based on your retention settings.
     - New backups will not be taken, unless and until the protection unit\(s\) are added to a custom policy or the Full Workload Backup policy is re-enabled.

   - Protection units included in other backup policies remain unaffected.

## Dynamic rules

Dynamic rules in Microsoft 365 Backup allow administrators to define backup policies based on distribution lists and security group memberships-eliminating the need for manual updates when group memberships change.

  


<iframe src="https://learn-video.azurefd.net/vod/player?id=7604db2b-5099-4b87-b94d-d36436b3ac18" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

  


Note

The dynamic rule feature is in preview.

### Delete a dynamic rule

When deleting a dynamic rule, you have two options that determine how existing accounts are treated in the backup policy.

#### Delete rule but continue backups

The dynamic rule is converted into a static list. Backup continues for all user accounts that were included through the rule at the time of deletion. However, future changes to the original distribution lists or security groups-such as users being added or removed-are no longer reflected in the backup policy. For example, if a user is added to a previously included group after the rule is deleted, they aren't automatically added to the backup policy.

#### Delete rule and stop new backups

The dynamic rule is removed, and no new backups are taken for accounts previously included through the rule. Existing backups for these users remain restorable until they expire based on the configured recovery window. You can re-enable backup for these users by manually adding them or by creating a new dynamic rule that includes them.

## States of backup

| States | Definition |
| --- | --- |
| Active | Protection scope selected under backup policy is being actively backed up. |
| Paused | No further backups are taken but already taken backups are preserved. |
| Not set up | No backup policy is set up for this scope. |
| Processing | A change to backup policy or a restore is in progress. |

## Multi-geo environments

Microsoft 365 Backup supports the backup of sites and user accounts from both the central and satellite locations if the multi-geo feature is enabled on your tenant. This means that you can add the sites or user accounts from all geos while creating the backup configuration policy via the CSV file upload method. Adding sites via the site picker, search, or filter rules don't currently support multi-geo. The user interface experiences today only support addition of sites in the tenant's central location.

Most importantly, data in the backups honor the multi-geo residency requirements and keep data in the geo you define for it to live.
