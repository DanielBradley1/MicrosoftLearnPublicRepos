<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/archive/archive-setup?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

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

Microsoft 365 Archive for SharePoint sites is now available for Government Community Cloud \(GCC\) organizations. To get started, configure a pay-as-you-go billing policy by following the guidance on [Setup and manage pay-as-you-go billing in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node) guide. After the billing policy is connected, enable SharePoint Site Archive from the Settings page.

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

Billing for unlicensed OneDrive accounts can also be enabled from the same **Microsoft 365 Archive** panel.

1. In the Microsoft 365 admin center, select [**Settings > Org settings**](https://go.microsoft.com/fwlink/p/?linkid=2171997).
2. On the **Org settings** page, select **Pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, select the **Settings** tab.
4. Under **Storage services**, select **Archive**.
5. On the **Microsoft 365 Archive** panel, in the **Manage archived unlicensed OneDrive accounts** section, select the status toggle to turn on Microsoft 365 Archive for unlicensed OneDrive accounts.
6. On the **Enable billing for unlicensed OneDrive accounts** panel, select **Confirm**.

## Turn off Microsoft 365 Archive

To turn off Microsoft 365 Archive:

1. On the **Pay-as-you-go services** page, select the **Settings** tab.
2. Under **Storage services**, select **Archive**.
3. On the **Microsoft 365 Archive** panel, in the **SharePoint site archive** section, select the status toggle to turn off Microsoft 365 Archive for SharePoint sites.
4. On the **Disable Microsoft 365 Archive** panel, select **Confirm**.

Billing for unlicensed OneDrive accounts can also be enabled separately.

5. On the **Microsoft 365 Archive** panel, in the **Manage archived unlicensed OneDrive accounts** section, select the status toggle to turn off Microsoft 365 Archive for unlicensed OneDrive accounts.
6. On the **Disable billing for unlicensed OneDrive accounts** panel, select **Confirm**.
