<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/ocr?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Set up and manage optical character recognition

Optical character recognition \(OCR\) is a pay-as-you-go service that is set up in the Microsoft 365 admin center.

## Prerequisites

### Licensing

Before you can use the OCR service, you must first link an Azure subscription in [pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide). OCR is billed based on the [type and number of transactions](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-pay-as-you-go-services?view=o365-worldwide).

### Permissions

You must be a [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) to be able to access the Microsoft 365 admin center and set up the OCR service.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Set up optical character recognition

After an [Azure subscription is linked to pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide), OCR will be automatically set up and enabled for all SharePoint sites.

### Set up data loss prevention policies using OCR

The compliance admin for your organization can also [configure the OCR settings for your tenant](https://learn.microsoft.com/en-us/microsoft-365/compliance/ocr-learn-about?view=o365-worldwide&#phase-3-configure-your-ocr-settings) for [data loss prevention policies](https://learn.microsoft.com/en-us/microsoft-365/compliance/dlp-learn-about-dlp?view=o365-worldwide) in the Microsoft Purview portal.

The compliance admin can specify which SharePoint sites to include for data loss prevention. If there are different sites specified for the service and data loss prevention, the maximum number of sites will be enabled for OCR. You won't be charged twice for processing.

For more information, see [Learn about optical character recognition in Microsoft Purview](https://learn.microsoft.com/en-us/microsoft-365/compliance/ocr-learn-about?view=o365-worldwide).

## Manage sites enabled for OCR

By default, the OCR service is turned on for libraries in all SharePoint sites. To limit which sites users can use OCR, follow these steps.

1. In the Microsoft 365 admin center, select [**Settings > Org settings**](https://go.microsoft.com/fwlink/p/?linkid=2171997).
2. On the **Org settings** page, select **Pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, select the **Settings** tab.
4. Under **Document & image services**, select **Optical character recognition**.
5. On the **Optical character recognition** panel, under **Select the SharePoint libraries where you would like to enable optical character recognition**, select **Edit**.
6. On the **Enable optical character recognition in Microsoft 365** panel, change the setting from **All sites** to **Selected sites \(up to 100\)** or **No sites**. For selected sites, follow the instructions to select the sites or upload a CSV listing of the sites. You can then manage site access permissions for the sites you selected.
7. Select **Save**.
