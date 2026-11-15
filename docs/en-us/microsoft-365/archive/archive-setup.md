<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/archive/archive-setup?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-21 -->

# Set up Microsoft 365 Archive

Microsoft 365 Archive follows a pay-as-you-go model, and is configured through the Microsoft 365 admin center.

[![Diagram showing four steps of the setup process for Microsoft 365 Archive.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-archive/archive-setup-diagram.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/m365-archive/archive-setup-diagram.png?view=o365-worldwide#lightbox)

To set up Microsoft 365 Archive, follow these steps:

1. Create an [Azure subscription](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/initial-subscriptions) and [resource group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal).
2. [Set up pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing) in the Microsoft 365 admin center.
3. [Turn on Microsoft 365 Archive](#set-up-microsoft-365-archive) in the Microsoft 365 admin center.
4. [Manage Microsoft 365 Archive for sites](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-manage?view=o365-worldwide) in the SharePoint admin center.

## Prerequisites

### Licensing

Before you can use Microsoft 365 Archive, you must first link your Azure subscription in [pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing). Microsoft 365 Archive is billed based on the number of gigabytes \(GB\) archived. For more information about pricing, see [Pricing model](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-pricing?view=o365-worldwide).

To set up pay-as-you-go billing, see [Configure for pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing).

### Permissions

You must be a [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) to be able to access the Microsoft 365 admin center and set up Microsoft 365 Archive.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Set up Microsoft 365 Archive

Note

Microsoft 365 Archive for SharePoint sites is also available for Government Community Cloud \(GCC\) organizations. For new configurations, use the Billing-node steps below to connect a pay-as-you-go billing policy.

### Turn on Microsoft 365 Archive in the Billing > Pay-as-you-go node \(after October 2026\)

For new configurations after October 2026, connect Microsoft 365 Archive to a pay-as-you-go billing policy in **Billing > Pay-as-you-go**. Connecting the policy turns on Archive in this flow. If your tenant uses the earlier **Setup > Billing and licenses > Activate pay-as-you-go services** flow, follow the [Setup-node billing instructions](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup) and the [enablement steps below](#turn-on-microsoft-365-archive-using-the-earlier-setup-flow) instead.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Billing > Pay-as-you-go**.
2. On the **Billing policies** tab, select **Add a billing policy**.
3. On the **Billing details** page, enter a policy name, select an Azure subscription and resource group, and choose a region. Read and accept the pay-as-you-go billing terms, and then select **Next**.
4. On the **Choose users** page, select **Next**. **All users** is applied automatically for services other than Microsoft Copilot pay-as-you-go services.
5. On the **Budget** page, optionally set a budget and alerts, and then select **Next**.
6. Review the details, and then select **Create policy**.
7. Select **Connect your services**, or go to the **Services** tab and find **Microsoft 365 Archive**. Select **Connect a policy**, turn on the **Connection status** toggle for the billing policy, and then select **Save**.

Microsoft 365 Archive is now enabled for your tenant.

#### Turn on billing for unlicensed OneDrive storage

Unlicensed OneDrive storage is a separate service in **Billing > Pay-as-you-go**. To enable billing for it, connect a billing policy separately:

1. In the Microsoft 365 admin center, go to **Billing > Pay-as-you-go**. If you need a new billing policy, create one by following steps 2 through 6 above.
2. On the **Services** tab, find **Unlicensed OneDrive storage** and select **Connect a policy**.
3. Turn on the **Connection status** toggle for the billing policy, and then select **Save**.

To keep unlicensed OneDrive accounts in standard storage, open the **Settings** tab for **Unlicensed OneDrive storage** and turn on **Standard storage**. To manage these accounts, [learn more about setting standard-storage period](https://learn.microsoft.com/en-us/sharepoint/standard-storage-unlicensed-onedrive-accounts#1-set-the-tenant-wide-standard-storage-period).

For more information about billing policies and budgets, see [Set up pay-as-you-go billing in the Billing node](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node).

### Turn on Microsoft 365 Archive using the earlier setup flow

Once pay-as-you-go billing is enabled in the Microsoft 365 admin center, Microsoft 365 Archive can be enabled.

1. In the Microsoft 365 admin center, select **[Settings > Org settings](https://go.microsoft.com/fwlink/p/?linkid=2171997)**.
2. On the **Org settings** page, select **Pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, select the **Settings** tab.
4. Under **Storage services**, select **Archive**.
5. On the **Microsoft 365 Archive** panel, in the **SharePoint site archive** section, select the status toggle to turn on Microsoft 365 Archive for SharePoint sites.
6. On the **Enable SharePoint archiving** panel, select **Confirm**.

Microsoft 365 Archive is now enabled for you. You're able to archive sites from the SharePoint admin center, and by default users can archive files on SharePoint sites.

Note

To manage file-level archive, see [Manage](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-manage?view=o365-worldwide).

To automatically archive inactive files, see [inactive files policies in SharePoint Advanced Management \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/archive/manage-inactive-files?view=o365-worldwide). The current preview requires SharePoint Advanced Management entitlement and PowerShell configuration; enabling Archive alone doesn't create a policy.

Billing for unlicensed OneDrive accounts can also be enabled from the same **Microsoft 365 Archive** panel.

1. In the Microsoft 365 admin center, select [**Settings > Org settings**](https://go.microsoft.com/fwlink/p/?linkid=2171997).
2. On the **Org settings** page, select **Pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, select the **Settings** tab.
4. Under **Storage services**, select **Archive**.
5. On the **Microsoft 365 Archive** panel, in the **Manage archived unlicensed OneDrive accounts** section, select the status toggle to turn on Microsoft 365 Archive for unlicensed OneDrive accounts.
6. On the **Enable billing for unlicensed OneDrive accounts** panel, select **Confirm**.

## Turn off Microsoft 365 Archive

### Disconnect services in the Billing node \(after October 2026\)

If you connected a billing policy in **Billing > Pay-as-you-go**, disconnect the service there rather than using the earlier **Pay-as-you-go services** settings toggles. You can disconnect Microsoft 365 Archive and unlicensed OneDrive storage independently.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Billing > Pay-as-you-go**, and then select the **Services** tab.
2. Select **Microsoft 365 Archive** to disconnect Archive, or select **Unlicensed OneDrive storage** to disconnect billing for unlicensed OneDrive accounts.
3. In the service side panel, select the **Billing policies** tab.
4. For the connected billing policy, turn off the **Connected** toggle in the **Connection status** column.
5. Select **Save**, and then close the side panel.

To turn off both services, repeat these steps for the other service. If both services use the same billing policy, disconnect each service separately. Disconnecting a service does not delete the policy or disconnect other services that use it. For more information, see [Disconnect a pay-as-you-go service](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node#disconnect-a-pay-as-you-go-service).

If you also enabled **Standard storage** for unlicensed OneDrive accounts, turn off **Standard storage** on the service **Settings** tab separately. Disabling Standard storage billing causes a custom tenant-wide active-storage period to revert functionally to 93 days. [Learn more about Standard storage for unlicensed OneDrive accounts](https://learn.microsoft.com/en-us/sharepoint/standard-storage-unlicensed-onedrive-accounts).

### Turn off services using the earlier setup flow

For tenants that use **Settings > Org settings > Pay-as-you-go services** to turn on Archive, turn it off in the same location:

1. In the Microsoft 365 admin center, go to **Settings > Org settings > Pay-as-you-go services**.
2. On the **Settings** tab, under **Storage services**, select **Archive**.
3. On the **Microsoft 365 Archive** panel, in the **SharePoint site archive** section, turn off the status toggle.
4. On the **Disable Microsoft 365 Archive** panel, select **Confirm**.

To turn off billing for unlicensed OneDrive accounts in the earlier setup flow:

1. In the Microsoft 365 admin center, go to **Settings > Org settings > Pay-as-you-go services**.
2. On the **Settings** tab, under **Storage services**, select **Archive**.
3. On the **Microsoft 365 Archive** panel, in the **Manage archived unlicensed OneDrive accounts** section, turn off the status toggle.
4. On the **Disable billing for unlicensed OneDrive accounts** panel, select **Confirm**.
