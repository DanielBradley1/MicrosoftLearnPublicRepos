<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Set up Microsoft 365 Backup

Tip

**Already have an Azure subscription and are a SharePoint Administrator or Global Administrator?** Follow these steps to quickly set up Microsoft 365 Backup in the admin center.  
  
[1. Set up pay-as-you-go billing](https://admin.microsoft.com/#/PaygPlatform)  
[2. Create backup policies to protect your data](https://admin.microsoft.com/#/Settings/enhancedRestore)  


  


Note

**Microsoft 365 Backup is now available to Government Community Cloud \(GCC\) customers.**

## Permissions

You must be a [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) to be able to access the Microsoft 365 admin center and set up Microsoft 365 Backup.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Create an Azure subscription

If you already have an Azure subscription and have Owner or Contributor access on the subscription, you can proceed to set up pay-as-you-go billing. If you need to create an Azure subscription, follow the guidance in [Create your Azure subscriptions](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/create-subscription) or [start creating a subscription on Azure](https://portal.azure.com/#view/Microsoft_Azure_Billing/CatalogBlade/appId/AddSubscriptionButton).

## 1. Set up pay-as-you-go billing

To set up pay-as-you-go billing, you need to have this information:

- **Valid Azure subscription**. An Azure subscription provides a logical container for your resources. Each Azure resource is associated with only one subscription. Creating a subscription is the first step in adopting Azure. To learn more about Azure, see [Azure fundamental concepts](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/fundamental-concepts).
- **Resource group**. A resource group provides a logical grouping of resources within an Azure subscription.
- **Region**. The region in which you want to register the service.
- **Owner or contributor**. Name of an owner or contributor role on the Azure subscription.

Once you have the information on this list, you're ready to begin. As a first step, you should link an Azure subscription in pay-as-you-go, if you haven't already done so.

**New Billing experience**

New customers onboarding to Microsoft 365 Backup after April 1, 2026 will use the new pay-as-you-go setup experience under the **Billing** node in Microsoft Admin Center. Follow the instructions on this page for [**Pay-as-you-go Setup**](https://go.microsoft.com/fwlink/?LinkId=2372125) to set up pay-as-you-go for Microsoft 365 Backup.

**Migrate billing Management from Org Settings to new Billing experience**

Existing customers who onboarded to Backup before April 1, 2026 who are interested in splitting Microsoft 365 Backup consumption into multiple Azure subscriptions can now migrate their billing management from Setup tab in Microsoft Admin Center using the new **Migrate** feature and then enable [Departmental Billing](https://go.microsoft.com/fwlink/?LinkId=2371547). We recommend customers migrate their billing management for Microsoft 365 Backup to the new billing experience to leverage some of the new Pay-as-you-go features like Budget alerts, create new Azure subscription or Resource group from Microsoft Admin Center etc. Read more about new [**Pay-as-you-go Setup**](https://go.microsoft.com/fwlink/?LinkId=2372125).

**Migrate**

Microsoft 365 Backup customers who currently have their billing managed under **Set up** -> **Org settings** should follow below steps to migrate their billing to new Billing experience.

1. In the Microsoft 365 admin center, select [**Setup**](https://go.microsoft.com/fwlink/p/?linkid=2171997) and then go to **Billing and licenses** section.
2. In the **Billing and licenses** section, select **Activate pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, on the **Settings** tab, select **Storage** and click on **Backup**.
4. In the panel that opens, click on **Migrate**

When you click on Migrate and confirm the billing policy details on screen, the experience will move the existing configuration of billing policy with same Azure subscription, Resource group and Region to a new billing policy with a temporary name *Service migration* in the new billing experience. You can edit the billing policy name later. While you migrate the billing policy, there will be no disruption to your existing backups. In case you do not see the Migrate option that means the feature is still being rolled out in your tenant.

**Edit your billing experience in Org Settings**

Existing customers in **Setup** can use the below steps to view or edit your existing billing setup.

1. In the Microsoft 365 admin center, select [**Setup**](https://go.microsoft.com/fwlink/p/?linkid=2171997), and then go to **Billing and licenses** section.
2. In the **Billing and licenses** section, select **Activate pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, on the **Settings** tab, select **Billing** to view and edit your existing pay-as-you-go settings.
4. To turn off Backup, go to **Settings** tab, click on **Backup** and toggle **Status** to Off.

**Departmental Billing Experience**

Now you can connect multiple billing policies to Backup and segment backup costs into different Azure subscriptions. You can connect more than one billing policies to Microsoft 365 Backup in the **Billing Policies** tab in Pay-as-you-go page. This will be ideal for organizations that prefer to breakdown their cost to different Azure subscriptions. If you prefer to manage Backup by departments, we recommend you enable [**Departmental Billing feature**](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing) \(link\).

## 2. Create backup policies to protect your data

Now that Microsoft 365 Backup is enabled for your organization, follow through to create policies and start protecting your content.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home).
2. Select **Settings**.
3. Select **Microsoft 365 Backup** from the list of products.

   ![Screenshot of the Microsoft 365 admin center panel showing Settings and Microsoft 365 Backup.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-setup-admin-center-panel.png?view=o365-worldwide)
4. [Create backup policies for OneDrive, SharePoint, or Exchange](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies?view=o365-worldwide#create-backup-policies).

## Enable email notifications

Email notifications help ensure that potentially harmful or important changes in Microsoft 365 Backup solution are brought to the attention of multiple people in your organization. This reduces the risk of critical actions going unnoticed.

When enabled, Microsoft 365 Backup sends email alerts to a **Backup Notification List** whenever an important backup event occurs. Global admins and Microsoft 365 Backup admins can turn on this feature and update the notification list at any time.

You can add up to 20 individual recipients to the list or include distribution lists and security groups. By default, recipients are notified only about potentially harmful events, but you can also opt in to receive notifications for routine events. Notifications are sent as a **daily email digest** when at least one relevant event occurs. If both notification types are enabled, you receive two separate emails-one for potentially harmful events and another for routine events.

### Events that trigger notifications

#### Potentially harmful events

- Disabling Microsoft 365 Backup
- Pausing billing due to issues or admin action
- Removing protection units from backup policies
- Offboarding protection units \(deletion of backups\)
- Pausing a backup policy
- Transferring backup controllers between Microsoft and third-party providers
- Revoking the Controller app
- Changing membership in the Backup Notification List
- Enabling or disabling the notifications feature

#### Routine events

- Creating or modifying backup policies
- Initiating or completing restores

Note

Jobs configured with a 10-minute RPO are not included in notification events. Notification events are triggered upon completion of the overall policy.

### Set up multi-admin notifications

1. Sign in to Microsoft 365 admin center as a Global admin, Microsoft 365 Backup admin, SharePoint admin, or Exchange admin.
2. Go to the **Email notifications** option on the **Microsoft 365 Backup** home page.

   ![Screenshot of the Microsoft 365 Backup page in the Microsoft 365 admin center showing the Email notifications option.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-email-notifications-option.png?view=o365-worldwide)
3. Turn on notifications.
4. Add users, distribution lists, or security groups \(only email enabled\) to the Backup Notification List.
5. \(Optional\) Select the checkbox to also receive routine event notifications.
6. Save your changes.

Note

We highly recommend enabling multi-admin notifications, at a minimum, for potentially harmful events.

## Admin roles and backup management privileges

Only tenant-level admins can create and manage backups using Microsoft 365 Backup for their users. End users don't have the ability to enable backup or restores for their user account, distribution lists, mailboxes, or sites. It's important to note that your admin role determines which products you can manage with Microsoft 365 Backup. We have also introduced a new dedicated role for this tool, the Microsoft 365 Backup Administrator, that can control the entire tool. For more information about this role, see [Microsoft 365 Backup Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#microsoft-365-backup-administrator).

| Admin role | OneDrive | SharePoint | Exchange |
| --- | --- | --- | --- |
| Global Administrator | ✓ | ✓ | ✓ |
| SharePoint Administrator | ✓ | ✓ |  |
| Exchange Administrator |  |  | ✓ |
| Microsoft 365 Backup Administrator | ✓ | ✓ | ✓ |

## Glossary

- **Protection units** - SharePoint sites, OneDrive accounts, or Exchange Online mailboxes backed up by the Microsoft 365 Backup tool.
- **Restore point** - A prior point in time from which you can restore a version of your content and metadata. If the protection unit from a prior point in time is identical to the present state of your data, then a restore from that point has no effect on your current data.
- **RPO** - Recovery point objective, or how close in time the most recent restore point is to an impacting event.
- **RTO** - Recovery time objective, or how fast a restore to a prior point in time might complete.
