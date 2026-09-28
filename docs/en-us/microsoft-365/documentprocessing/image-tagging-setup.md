<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/image-tagging-setup?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Set up and manage enhanced image tagging in SharePoint

Image tagging is a pay-as-you-go service that is set up in the Microsoft 365 admin center.

## Prerequisites

### Licensing

Before you can use image tagging, you must first link an Azure subscription in [pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide). Image tagging is billed based on the [type and number of transactions](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-pay-as-you-go-services?view=o365-worldwide).

### Permissions

You must be a [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) to be able to access the Microsoft 365 admin center and set up image tagging.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Set up image tagging

After an [Azure subscription is linked to pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide), image tagging is automatically set up and enabled for all SharePoint sites.

Although you enable pay-as-you-go billing for image tagging, you're charged only when [image tagging is enabled on a document library](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/image-tagging?view=o365-worldwide).

## Manage sites

By default, image tagging is available for libraries on all SharePoint sites. To limit which sites users can apply image tagging, follow these steps.

1. In the Microsoft 365 admin center, select [**Settings > Org settings**](https://go.microsoft.com/fwlink/p/?linkid=2171997).
2. On the **Org settings** page, select **Pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, select the **Settings** tab.
4. Under **Document & image services**, select **Image tagging**.
5. On the **Image tagging** panel, under **Which SharePoint sites should show the option to enable image tagging**, select **Edit**.
6. On the **Image tagging** panel, change the setting from **Libraries in all SharePoint sites** to **Selected sites \(up to 100\)** or **No sites**. For selected sites, follow the instructions to select the sites or upload a CSV listing of the sites. You can then manage site access permissions for the sites you selected.
7. Select **Save**.
