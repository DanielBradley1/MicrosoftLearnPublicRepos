<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/backup/backup-billing?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Departmental Billing for Microsoft 365 Backup

If you're a large organization with multiple departments and want to manage Microsoft 365 Backup within departments or groups, departmental billing may be the right fit for you. With Departmental billing, you can manage Backup with the following features:

1. Breakdown backup costs by different Azure subscriptions.
2. Limit Backup management \(creation and update\) to certain admins within departments with Role-based-access-control\(RBAC\).
3. Prevent admins from another department using your Azure subscription to cause unapproved backup charges.

**Role-Based-Access-Control within departments\(RBAC\)**: To limit admins who can manage Backup within a department or group, every backup admin should also have an Owner or Contributor role on the subscription. This way only an approved admin who is given spending power on a subscription can create and edit backups and cause consumption to the department's Azure subscription. If you're an owner for the department's subscription, we recommend giving the lower privileged 'Contributor' role to backup admins in your department if they don't need privileges to add other admins to the subscription.

### Set up departmental billing

To set up departmental billing for your tenant, follow these steps.

1. Create billing policies and connect them to Microsoft 365 Backup following the instructions in [**Pay-as-you-go Setup**](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node) for Microsoft 365 Backup.
2. In the **Services** tab of **Pay-as-you-go** page, select **Microsoft 365 Backup**.
3. To enable departmental billing, in the **Settings** tab of Microsoft 365 Backup page, select the checkbox for limiting management of Backup within departments.

   ![Screenshot of the settings tab for Microsoft 365 Backup.](https://learn.microsoft.com/en-us/microsoft-365/backup/media/31bdf6c3-966f-40ce-8abf-f144ed2fe893.png?view=o365-worldwide)

   Now that departmental billing with Backup is enabled for your tenant, Admins are assigned Owner / Contributor Azure roles to the billing policies connected to Backup can only create and edit backup policies.
4. You can create backup for your department by creating [**backup policies as outlined here**](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup#2-create-backup-policies-to-protect-your-data). In Create / Edit policy wizard, admins need to associate a Billing Policy with a Backup Policy. In the billing policy list, admins are shown only billing policies that they have Owner/Contributor access.  
   ![Screenshot of assigning a billing policy to a backup policy.](https://learn.microsoft.com/en-us/microsoft-365/backup/media/91221de4-63e8-41a2-a2c4-528faa38b296.png?view=o365-worldwide)

Note

**Once you have enabled departmental billing, admins who have been assigned Owner / Contributor Azure roles to the billing policies connected to Backup can only create and edit backup policies.**

Admins who don't have role-based access control \(RBAC\) rights to your backup policies won't be able to use your billing policy to create backup policies or edit backup policies created by admins in your department. Billing policies show as **Confidential** for admins who don't have access.

![Screenshot of backup policy list showing a billing policy as confidential.](https://learn.microsoft.com/en-us/microsoft-365/backup/media/07ba1426-fe4a-4023-8ebd-ab4904f2d789.png?view=o365-worldwide)

### Change Billing policies associated with Backup policies

Once a Billing Policy is associated with a Backup Policy, it can be updated from the Backup Dashboard

1. Select the Backup policy you want to update the Billing Policy. Select the 3-dots next to backup policy name and select **Update Billing policy**.  ![Screenshot of changing the billing policy for a backup policy.](https://learn.microsoft.com/en-us/microsoft-365/backup/media/510a8756-113d-4403-941a-8366366d1800.png?view=o365-worldwide)

### Disable departmental billing

If you wish to manage Backup without the RBAC control of restricting Backup management to Owner or Contributor of subscriptions, uncheck the box in Settings tab Microsoft 365 Backup page.

### Manage consumption and invoices for Microsoft 365 Backup

You can view actual and accumulated cost breakdown by tenants and service type for OneDrive, SharePoint, and Exchange in Microsoft Cost Management in the Azure portal or by accessing the [Cost Management public APIs](https://learn.microsoft.com/en-us/rest/api/cost-management/operation-groups). Cost breakdown by application ID is coming soon.

  


<iframe src="https://learn-video.azurefd.net/vod/player?id=a87d77a7-2c88-43fc-ae8c-5ba42765f956" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

  


1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Search for *Cost Management + Billing*.
3. Select **Cost analysis** to see:

   - Accumulated cost and forecast cost.
   - Select **+Add Filter** to see breakdown of cost by meters and tags.

     ![Screenshot of the cost analysis page in Microsoft Cost Management.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-cost-analysis.png?view=o365-worldwide)

You can also export daily cost information using billing export feature in Azure portal. For more information, see [Tutorial: Create and manage exported data](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-export-acm-data?tabs=azure-portal).

### Billing attribution by tenants, service type, and applications

You can see actual cost breakdown by tags in Azure portal. There are currently three tags available for Microsoft 365 Backup: **tenants**, \*\*servicetype, and **protectionunitid**.

To view tags:

1. Select **+Add Filter** to see breakdown of cost by meters and tags.
2. Select the tag:

   - In the key-value pair, select **tenants** or **servicetype**, and then select the respective tenant ID or service type.

     - **tenants** shows a list of tenant IDs.
     - **servicetype** is OneDrive, SharePoint, or Exchange.
     - **applications** shows a list of app IDs.
     - **protectionunitid** shows a list of Site IDs.
     - Exchange mailbox - Mailbox ID of mailbox backed up. Note this attribution is only available on explicit admin consent as detailed in section **Billing attribution for Exchange Mailbox**.
     - OneDrive account - SiteId of the corresponding OneDrive site.
     - SharePoint site - SiteId of the corresponding SharePoint site.

   - Azure cost analysis - filter by tag.
   - The tag for OneDrive is its siteID. To convert this back to a userID, you can use the following API: `https://graph.microsoft.com/v1.0/sites/<siteid>/drive?select=owner`

3. In the left navigation, select **Billing** to see monthly invoices.

   We recommend using this view to see the costs by resources for Microsoft 365 Backup.

   ![Screenshot of the recommended view to see costs by resources in Microsoft Cost Management.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-backup/backup-cost-by-resources-view.png?view=o365-worldwide)
4. Set up budget alerts on cost by following the steps in the [Cost Management public APIs](https://learn.microsoft.com/en-us/rest/api/cost-management/operation-groups).

### Billing attribution for Exchange Mailbox Consent

In Azure Cost Management, SharePoint and OneDrive cost attribution by siteIDs are included by default. If you want to see cost attribution of your Microsoft 365 Backup consumption by mailboxes in Azure Cost Management, you need to enable a settings and give consent to send mailbox ID to Azure services as part of a Microsoft 365 privacy requirement. This settings is not applicable for cost attribution by siteID. You can follow the instructions below to enable cost attrubution by mailbox ID and provide consent. We recommend you read the consent language carefully before enabling the cost attrubition by mailbox settings.

1. In Microsoft 365 Backup home page, click on the three dots on **Exchange** and select **Settings**
2. In the panel that opens, read the consent language and select the checbox if you agree with Exchange mailbox ID being sent to Azure.

Warning

The **MailboxDbGuid** tag in the Azure consumption report is intended for Microsoft internal use only. We recommend that you don't rely on it because its value might change. Note that this is different from the MailboxId.
