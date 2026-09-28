<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/archive/archive-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Overview of Microsoft 365 Archive

Microsoft 365 Archive provides cost-effective storage for inactive SharePoint files and sites.

Organizations often need to retain inactive or aging data for long periods in case they need to retrieve it later. Storing this data in SharePoint helps simplify searchability, security, compliance, and data lifecycle management.

Microsoft 365 Archive allows you to retain inactive data by moving it into a cold storage tier within SharePoint. Data archived with Microsoft 365 Archive automatically retains the same searchability, security, and [compliance](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-compliance?view=o365-worldwide) standards at a reduced cost.

Note

Microsoft 365 Archive for SharePoint sites is now available for Government Community Cloud \(GCC\) organizations. To get started, configure a pay-as-you-go billing policy by following the guidance on [Setup and manage pay-as-you-go billing in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node) guide. After the billing policy is connected, enable SharePoint Site Archive from the Settings page.

Other advantages of using Microsoft 365 Archive include:

- **Copilot optimization** - Copilot is not trained on archived content, maximizing response relevancy.
- **Cost savings** - A lower list price on storage consumption beyond your license-allocated Microsoft 365 storage quota.
- **Lossless metadata** - A site retains all of its metadata and permissions upon reactivation.
- **Speed** - Ultra-fast archive of sites of any size and any number of sites.
- **Decluttering** - Explicit separation between active and inactive content to help manage your site's lifecycle.

Microsoft 365 Archive works with the Microsoft 365 search index and the [Microsoft Purview](https://learn.microsoft.com/en-us/purview/purview) feature set to support long-term data management at a price aligned with the lifecycle of your content. Microsoft 365 Archive is managed in the SharePoint admin center by [SharePoint Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

When a file or site is archived, it moves into an explicitly colder tier and no longer consumes the tenant's active storage quota. Instead, it contributes to Microsoft 365 Archive storage consumption. Content in this tier is no longer directly accessible to anyone. Full content search works for Purview Content Search, end-user search, and eDiscovery search experiences. Purview Content Search and eDiscovery can still directly export content but may take longer to export archived content.

When a site is archived, all content within the site is archived, including:

- Document libraries, folder structures, and files
- Lists and list data
- Permissions and all metadata

Administrators should notify site owners and end users before archiving a site so they're aware that the site will no longer be accessible.

## Limitations

### Site Archive limitations

- Publishing sites, channel sites, and some legacy site template types aren't available to archive with Microsoft 365 Archive. For more information, see [Site templates supported](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-manage?view=o365-worldwide#site-templates-supported).
- Sites associated with Teams that use only standard channels are supported for archiving. Sites associated with Teams that include private or shared channels are only partially supported:

  - SharePoint admin center: Archiving a site with channel sites is not possible. \(Message: "The group connected site with channel sites associated can't be archived."\)
  - PowerShell and Graph API: Archiving a site with channel sites isn't blocked. Only the main site associated with the Team \(and its standard channels\) is archived. The private and shared channel sites remain active. Archiving the channel sites directly is not possible, as these sites use unsupported site templates.

### File Archive limitations

- Some Microsoft 365 applications and services don't yet support file-level archiving. These applications might display incorrect error messages, fail to load correctly, or fail actions taken with archived content. Because client support and user awareness for archived files continue to evolve, we recommend that you use file-level archive thoughtfully and ensure users understand how to reactivate files at their original location if access is required—especially if they encounter unexpected open or load errors. The list of known limitation includes, but isn't limited to:

  - Word for the web and PowerPoint for the web.
  - Teams, OneDrive, and SharePoint mobile applications.
  - macOS with the OneDrive sync client.
  - Older versions of Windows, such as Windows 10 and earlier, with the OneDrive sync client.
  - This limitation also applies to Windows devices that aren't configured to receive frequent updates.
  - Older versions of Office desktop apps that haven't had updates since March 1, 2026.
  - Other apps such as Clipchamp and Power BI fail to load archived content when attempting to import.

- File-level archive is available only for SharePoint sites. When archived files are copied or moved, they retain their archived state. However, if an archived file is moved or copied into OneDrive, that archived state might not always be visually represented in the OneDrive user interface.
- Files that are reactivated cannot be archived again for 120 days.
- Certain file types can't be archived, including OneNote, SharePoint pages, and SharePoint agents.
- The Site Assets library on SharePoint sites does not support file-level archive.

## Related article

- [Education offering](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-education-offering?view=o365-worldwide)
