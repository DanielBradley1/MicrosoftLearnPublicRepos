<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/add-storage-space?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-01 -->

# Add more OneDrive and SharePoint storage to your Microsoft 365 subscription

If your organization starts to run out of storage for your OneDrive accounts or SharePoint sites, several options are available to add more storage capacity:

- [Microsoft 365 OneDrive Storage](#add-microsoft-365-onedrive-storage)
- [OneDrive Extra Storage](#add-onedrive-extra-storage)
- [Microsoft 365 SharePoint Storage](#add-microsoft-365-sharepoint-storage)
- [Office 365 Extra File Storage](#add-office-365-extra-file-storage)

Note

- If you bought your subscription through Volume Licensing or a Cloud Solution Provider \(CSP\), you can't buy **Office 365 Extra File Storage** directly from Microsoft. For help, contact your representative or partner.
- For information about OneDrive storage, see [Set the default storage space for OneDrive users](https://learn.microsoft.com/en-us/onedrive/set-default-storage-space).

## Before you begin

Microsoft 365 OneDrive Storage and Microsoft 365 SharePoint Storage share the same prerequisites, while OneDrive Extra Storage and Office 365 Extra File Storage have different prerequisites. For details about the specific prerequisites for each option, see the relevant prerequisites sections later in this article.

## Add Microsoft 365 OneDrive Storage

Note

Microsoft 365 OneDrive Storage enters public preview in July 2026 and will be available to all commercial customers. This product isn't currently available to education, GCC, or Microsoft 365 operated by 21Vianet in China customers.

Microsoft 365 OneDrive Storage is a pay-as-you-go service that provides flexible billing to add storage to your OneDrive accounts. Use and pay for more storage above the account's licensed quota. To learn more about pay-as-you-go services, see [Pay-as-you-go services overview](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-services?view=o365-worldwide). To monitor usage and receive alerts as costs approach defined thresholds, see [Create a budget for pay-as-you-go billing in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-budget?view=o365-worldwide).

### Prerequisites for adding Microsoft 365 OneDrive Storage

Before you set up Microsoft 365 OneDrive Storage, make sure you meet the following prerequisites:

- You must have an [Azure subscription](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/initial-subscriptions) and resource group.
- You must have the Owner or Contributor role to an Azure subscription and a resource group linked to the same Azure subscription. For more information, see [Use the Azure portal and Azure Resource Manager to Manage Resource Groups](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal).
- To access the Microsoft 365 admin center, you must have either the SharePoint Administrator or Global Administrator role.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

### Set up pay-as-you-go billing for Microsoft 365 OneDrive Storage

To set up pay-as-you-go billing for Microsoft 365 SharePoint Storage, follow the steps in [Set up or disconnect pay-as-you-go in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node?view=o365-worldwide). When you reach "Step 4. Review and create the billing policy," select the **Microsoft 365 OneDrive Storage** service.

### Update storage limits for select users

After you set up pay-as-you-go billing, [change the specific user's OneDrive storage space](https://learn.microsoft.com/en-us/sharepoint/change-user-storage). When you set up pay-as-you-go billing, you can set a storage limit that's higher than the licensed quota. The maximum value remains at 25,600 GB. Only the storage usage above the licensed quota is billed.

### Disconnect Microsoft 365 OneDrive Storage

To stop using Microsoft 365 OneDrive storage, follow the steps in [Disconnect pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup?view=o365-worldwide#disconnect-pay-as-you-go-billing). If you disconnect while OneDrive accounts are over their licensed quota, enforcement of the quota resumes.

## Add OneDrive Extra Storage

If a user needs more OneDrive storage, you can buy OneDrive Extra Storage in the Microsoft 365 admin center. The exact purchase steps depend on your billing account type. After you buy OneDrive Extra Storage, assign the purchased capacity to a licensed user like any other add-on license.

OneDrive Extra Storage is sold as capacity packs in 100-GB, 500-GB, and 1-TB through 6-TB sizes. You can later unassign, reassign, or cancel capacity packs as needed. A capacity pack can't be split across multiple users. It doesn't replace the user's existing OneDrive license. A single user's total storage can't exceed 25-TB. If you configured a lower storage limit for the user, update that limit separately so the user can use the added capacity.

### Prerequisites for adding OneDrive Extra Storage

- [Find out what type of billing account you have](https://learn.microsoft.com/en-us/microsoft-365/commerce/manage-billing-accounts?view=o365-worldwide#view-my-billing-accounts).
- If you have a Microsoft Customer Agreement \(MCA\) billing account type, you must be a Billing account owner or contributor, or a Billing profile owner or contributor to complete the tasks described in this article. For information about billing account and billing profile roles, see [Understand your Microsoft business billing account](https://learn.microsoft.com/en-us/microsoft-365/commerce/manage-billing-accounts?view=o365-worldwide) and [Manage your Microsoft business billing profiles](https://learn.microsoft.com/en-us/microsoft-365/commerce/billing-and-payments/manage-billing-profiles?view=o365-worldwide).
- If you have a Microsoft Online Subscription Agreement \(MOSA\), you must be at least a Billing Administrator to complete the tasks described in this article. For more information, see [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

Note

If you're the person who signed up for the subscription, you're automatically a Billing account owner.

### Buy OneDrive Extra Storage

**If you have an MCA billing account type:**

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

   - If you're using the **Simplified view**, select **Billing**, and then select **Add more products**.
   - If you're using the **Dashboard view**, go to the [Marketplace](https://go.microsoft.com/fwlink/p/?linkid=868433) page.

2. Under **View by category**, select **Office 365**.
3. Find **OneDrive Extra Storage**, and then select **Details**.
4. Select the plan with the amount of storage that you want: select a subscription length and billing frequency, select the license quantity, and then select **Buy**.
5. In the **Checkout** panel, choose the billing profile that you want to use, or add a new one. The **Purchase information** section lists the cost and subscription term.
6. Review your order, and then select **Place order**.

**If you have an MOSA billing account type:**

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

   - If you're using the **Simplified view**, select **Billing**.
   - If you're using the **Dashboard view**, go to the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page.

2. Select the subscription that you want to buy an add-on for.
3. On the subscription details page, in the **Add-ons** section, select **Find more add-ons in Marketplace**.
4. Find **OneDrive Extra Storage**, and then select **Details**. Select the product with the amount of storage that you want.
5. From the drop-down list, select the subscription to connect with the add-on, and then select **Connect to subscription**.
6. On the **Checkout** page, enter the quantity that you want to buy, and then select **Place order**.

## Add Microsoft 365 SharePoint Storage

Note

As of June 2026, Microsoft 365 SharePoint storage is in public preview for all commercial tenants. This product isn't currently available to education, GCC, or Microsoft 365 operated by 21Vianet in China customers.

Microsoft 365 SharePoint Storage is a pay-as-you-go service that provides flexible billing to add storage to your SharePoint sites. Use and pay for more storage above the storage quota as needed. To learn more about pay-as-you-go services, see [Pay-as-you-go services overview](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-overview?view=o365-worldwide). To monitor usage and receive alerts as costs approach defined thresholds, see [Create a budget for pay-as-you-go billing in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-budget?view=o365-worldwide).

While your tenant is enrolled in Microsoft 365 SharePoint Storage, you don't receive quota-related email notifications and banner notifications in the SharePoint admin center because the tenant is considered within quota.

### Prerequisites for adding Microsoft 365 SharePoint Storage

Before you set up Microsoft 365 SharePoint Storage, you must meet certain prerequisites. These prerequisites are the same as the ones for Microsoft 365 OneDrive Storage. For details about these shared prerequisites, see [Prerequisites for adding Microsoft 365 OneDrive Storage](#prerequisites-for-adding-microsoft-365-onedrive-storage).

### Set up pay-as-you-go billing for Microsoft 365 SharePoint Storage

To set up pay-as-you-go billing for Microsoft 365 SharePoint Storage, follow the steps in [Set up or disconnect pay-as-you-go in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node?view=o365-worldwide). When you reach "Step 4. Review and create the billing policy," select the **Microsoft 365 SharePoint Storage** service.

Note

If you have a multi-geo tenant that uses pay-as-you-go storage, billing is based on the tenant's storage quota, not each geo's quota. Billing starts when the tenant's total storage usage across all geos **exceeds** the tenant quota.

### Disconnect Microsoft 365 SharePoint Storage

To stop using Microsoft 365 SharePoint storage, follow the steps in [Disconnect pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup?view=o365-worldwide#disconnect-pay-as-you-go-billing). If you disconnect while your tenant is over its storage quota, enforcement of the quota resumes immediately.

## Add Office 365 Extra File Storage

Use the Office 365 Extra File Storage add-on to add more storage in 1-GB increments. You can buy the add-on in the Microsoft 365 admin center. If you don't see **Office 365 Extra File Storage** in the list of available add-ons, it means that your plan isn't eligible to buy it. For more information, see [Is my plan eligible?](#is-my-plan-eligible-for-office-365-extra-file-storage)

### View available SharePoint storage

1. Go to the [SharePoint admin center](https://go.microsoft.com/fwlink/p/?linkid=2185219) and sign in with an account that has SharePoint admin permissions for your organization.
2. In the navigation menu, select **Active sites**.
3. The top of the **Active sites** page displays the amount of storage used across all sites, and the total storage for your subscription. If your organization configured multi-geo in Microsoft 365, the bar also shows the amount of storage used across all geographical locations.

Note

The storage used doesn't include changes made within the last 24-48 hours. SharePoint storage is calculated in binary Gigabytes \(GB\), where 1 GB = 22<sup>30</sup> bytes.

After you determine how much storage you're using, you can add or remove storage space for your subscription. To find out how much it costs to add storage space, follow the steps in this article and review the pricing information before you buy more.

For information about setting site collection storage limits, see [Manage site collection storage limits](https://learn.microsoft.com/en-us/sharepoint/manage-site-collection-storage-limits).

### Prerequisites for adding Office 365 Extra File Storage

Before you set up Office 365 Extra File Storage, you must meet certain prerequisites. These prerequisites are the same as the ones for OneDrive Extra Storage. For details about these shared prerequisites, see [Prerequisites for adding Microsoft 365 OneDrive Storage](#prerequisites-for-adding-microsoft-365-onedrive-storage).

### Buy the Office 365 Extra File Storage add-on

**If you have an MCA billing account type:**

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

   - If you're using the **Simplified view**, select **Billing**, and then select **Add more products**.
   - If you're using the **Dashboard view**, go to the [Marketplace](https://go.microsoft.com/fwlink/p/?linkid=868433) page.

2. Under **View by category**, select **Office 365**.
3. Find **Office 365 Extra File Storage**, and then select **Details**. Enter the number of gigabytes of storage that you want, select a subscription length and billing frequency, and then select **Buy**.
4. In the **Checkout** panel, choose the billing profile that you want to use, or add a new one. The **Product name** section lists the cost, subscription term, and the renewal date for the subscription. To match the renewal date with another subscription paid by the billing profile, select **Select a different renewal date**.
5. Review your order, and then select **Place order**.

**If you have an MOSA billing account type:**

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

   - If you're using the **Simplified view**, select **Billing**.
   - If you're using the **Dashboard view**, go to the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page.

2. Select the subscription that you want to buy an add-on for.
3. On the subscription details page, in the **Add-ons** section, select **Find more add-ons in Marketplace**.
4. Find the **Office 365 Extra File Storage** add-on, and then select **Details**.
5. From the drop-down list, select the subscription to connect with the add-on, and then select **Connect to subscription**.
6. On the **Checkout** page, enter the quantity that you want to buy and then select **Place order**.

### Increase or decrease your extra file storage

If you already bought extra file storage through the Office 365 Extra File Storage add-on, use the following steps to increase or decrease the extra storage space for your subscription. You can reduce the storage to as low as 1 GB. To remove all of the extra storage space, [contact support](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support?view=o365-worldwide).

**If you have an MCA billing account type:**

1. Go to the [admin center.](https://go.microsoft.com/fwlink/p/?linkid=2024339)

   - If you're using the **Simplified view**, select **Billing**.
   - If you're using the **Dashboard view**, go to the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page.

2. Select **Office 365 Extra File Storage**.
3. On the product details page, select **Buy licenses** or **Remove licenses**.
4. In the **Buy licenses** or **Remove licenses** panel, choose whether you want the change to happen now or when the subscription renews.
5. In the **New quantity** section, enter the number of GBs of storage space that you want for the subscription.
6. Select **Save**.

**If you have an MOSA billing account type:**

1. Go to the [admin center.](https://go.microsoft.com/fwlink/p/?linkid=2024339)

   - If you're using the **Simplified view**, select **Billing**.
   - If you're using the **Dashboard view**, go to the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page.

2. Select the subscription that contains the Office 365 Extra File Storage add-on.
3. On the product details page, in the **Add-ons** section, select **Manage add-ons**.
4. In the **Manage add-ons** panel, from the **Add-on** list, choose **Office 365 Extra File Storage**.
5. In the **Quantity** text box, enter the number of GBs of storage space that you want for the subscription.
6. Select **Save**.

### Is my plan eligible for Office 365 Extra File Storage?

Office 365 Extra File Storage is available for the following subscriptions:

- Microsoft 365 Business Basic
- Microsoft 365 Business Premium
- Microsoft 365 Business Standard
- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 F1
- Microsoft 365 F3
- Microsoft 365 for the web with SharePoint Plan 1
- Microsoft 365 for the web with SharePoint Plan 2
- Office 365 Enterprise E1
- Office 365 Enterprise E2
- Office 365 Enterprise E3
- Office 365 Enterprise E5
- Office 365 A3 \(faculty\)
- Office 365 A5 \(faculty\)
- SharePoint Online Plan 1
- SharePoint Online Plan 2

Note

Office 365 Extra File Storage is also available for GCC, GCC High, and DOD plans.

## Next steps

After you buy more storage, remember to [assign the new licenses to users](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide).

## FAQ

### Can our tenant have both Microsoft 365 SharePoint Storage and Office 365 Extra File Storage?

Yes. These options work well together. Office 365 Extra File Storage increases the tenant storage quota, while Microsoft 365 SharePoint Storage allows SharePoint storage to grow without triggering quota enforcement concerns.

### What happens if you have both Microsoft 365 SharePoint Storage and Microsoft 365 Archive?

Microsoft 365 SharePoint Storage is intended for active content that requires ongoing collaboration and updates, whereas Microsoft 365 Archive is designed for inactive content that must be retained without modifications. The system automatically optimizes billing based on whether storage is classified as active or archived. Any active or archived storage usage that exceeds the tenant quota is billed through the applicable product at the most cost-effective rate.

### How does changing the OneDrive user storage limit affect billing?

After you connect Microsoft 365 OneDrive Storage to a billing policy, you can control how much a user's OneDrive can grow by setting that user's storage limit. For example, if a user has a licensed quota of 1-TB, and you increase the storage limit to 3-TB, the user's OneDrive can grow up to 3-TB. Only usage above the licensed 1-TB quota is billed. If the user consumes 1.5-TB, the other 0.5-TB is billable.

## Related content

[Manage site storage limits in SharePoint in Microsoft 365](https://learn.microsoft.com/en-us/sharepoint/manage-site-collection-storage-limits) \(article\)
