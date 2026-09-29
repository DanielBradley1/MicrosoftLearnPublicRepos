<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/activity-privacy -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Configure activity monitoring to protect user privacy

Learn how to configure activity privacy in Microsoft Defender for Cloud Apps to monitor users while complying with your organization's privacy regulations. This article covers how to set up privacy user groups, assign admin permissions to view private activities, and view those activities in the activity log.

## Activity privacy overview

Microsoft Defender for Cloud Apps allows enterprises to granularly determine which users they want to monitor based on group membership. Activity privacy will enable you to follow your organization's compliance regulations without compromising user privacy. Activity privacy is achieved by allowing you to monitor users while maintaining their privacy by hiding their activities in the activity log. Only authorized admins can choose to view these private activities, with each instance being audited in the governance log.

Note

Private activities aren't forwarded to Microsoft Defender XDR Advanced hunting, and aren't passed on in our SIEM integration.

## Configure activity privacy user groups

You may have users in Defender for Cloud Apps that you want to monitor, but, due to compliance regulations, you need to limit the people who can do so. Activity privacy lets you define a user group for which activities performed by members of that group will be hidden by default.

To configure your user privacy groups, you must first [import user groups](https://learn.microsoft.com/en-us/defender-cloud-apps/user-groups) to Defender for Cloud Apps. By default, you'll see the following groups:

- **Application** user group - A built-in group that enables you to see activities performed by Microsoft 365 and Microsoft Entra applications.
- **External users** group - All users who aren't members of any managed domains you configured for your organization.

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **System**, select **Scoped deployment and privacy**.
2. To set specific groups to be monitored by Defender for Cloud Apps, in the **Activity privacy** tab, select **+Add group**.
3. In the **Add user groups** dialog, under **Select user groups**, select all the groups you want to make private in Defender for Cloud Apps, then select **Add**.

   ![Screenshot of the Add user groups dialog for selecting groups to make private in Defender for Cloud Apps.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/activity-privacy-add-user-groups.png)


   Note


   Once a user group is added, all the activities performed by users of the group will be made private from then on. Existing activities are not affected.

## Assign admins permission to view private activities

To grant specific admins permission to view private activities, follow these steps:

1. In the Microsoft Defender Portal, in the left-hand menu, select **Permissions**.
2. Under **Cloud Apps**, choose **Activity Privacy Permissions**.

   ![Configure Activity Privacy Permissions.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/activity-privacy-permissions.png)
3. To give specific admins permission to view private activities, in the **Activity privacy permissions** tab, select **+Add user**.
4. In the **Add admin permission** dialog, enter the admin's UPN or email address and select **Add permission**.

   ![Screenshot of the dialog for granting admins permission to view private activities.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/activity-privacy-add-admin-permission.png)


   Note


   Only admins can be assigned permission to view private activities.

## View private activities

Once an admin has been granted the appropriate permission to view private activities, the admin can choose to see those activities in the activity log.

### View private activities in the activity log

1. In the **Activity log** page, to the right of the activity table, select **Table settings**, and then select **Show private activities**.

   ![Screenshot of the Activity log settings control used to open privacy viewing settings.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/activity-privacy-view-settings-icon.png)

2. In the **Show private activities** dialog, select **OK** to confirm that you understand that showing private activities is being audited. Once confirmed, the private activities are shown in the activity log, and the action of showing private activities is recorded in the governance log.

Tip

When you export activities with the **Show private activities** option selected, the activities inside the export are still private, and no activity details are exposed.

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [contact Microsoft Defender XDR support](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
