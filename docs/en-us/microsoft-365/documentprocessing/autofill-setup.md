<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/autofill-setup?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Set up and manage autofill columns

Autofill columns is a pay-as-you-go service that is set up in the Microsoft 365 admin center.

Note

**Autofill columns is included as part of Knowledge Agent \(preview\) in SharePoint.**  
Tenants who have enabled Knowledge Agent can use Autofill columns as part of this preview experience. Knowledge Agent is a built-in SharePoint capability designed to help your organization prepare content for AI and is included with the Microsoft Copilot license. During the **preview**, Autofill is visible only to users with an eligible Microsoft Copilot license and do not require a separate Syntex pay-as-you-go setup. For more information, see [Get started with Knowledge Agent \(preview\)](https://learn.microsoft.com/en-us/sharepoint/knowledge-agent-get-started).

## Prerequisites

### Licensing

Before you can use autofill columns, you must first link an Azure subscription in [pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide). The autofill columns service is billed based on the [type and number of transactions](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-pay-as-you-go-services?view=o365-worldwide).

### Permissions

You must be a [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) to be able to access the Microsoft 365 admin center and set up autofill columns.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Set up autofill columns

After an [Azure subscription is linked to document processing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide), autofill columns is automatically set up and turned on for all SharePoint sites.

## Manage sites

By default, the autofill columns service is turned on for libraries in all SharePoint sites. To limit which sites users can use autofill columns, follow these steps.

1. In the Microsoft 365 admin center, select [**Settings > Org settings**](https://go.microsoft.com/fwlink/p/?linkid=2171997).
2. On the **Org settings** page, select **Pay-as-you-go services**.
3. On the **Pay-as-you-go services** page, select the **Settings** tab.
4. Under **Document & image services**, select **Autofill columns**.
5. On the **Autofill columns** panel, under **Sites where Autofill can be used when it's turned on**, select **Edit**.
6. On the **Sites where models can be created** panel, change the setting from **All sites** to **Selected sites \(up to 100\)** or **No sites**. For selected sites, follow the instructions to select the sites or upload a CSV listing of the sites. You can then manage site access permissions for the sites you selected.
7. Select **Save**.
