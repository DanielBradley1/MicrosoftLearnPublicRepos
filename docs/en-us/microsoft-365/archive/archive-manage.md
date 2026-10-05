<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/archive/archive-manage?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-24 -->

# Manage Microsoft 365 Archive

## Archive a file

On sites with file-level archive enabled, users can manually archive files that they have edit permissions for. Users select one or more files and choose the '***Archive***' action. After a file is archived, it requires reactivation before it can be read. Files that were recently archived can be reactivated instantly.

To learn more about archive states, see [Archive states in Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-states?view=o365-worldwide).

## Archive a site

[SharePoint Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) can archive both non-group-connected sites and group-connected sites from the SharePoint admin center. When a group-connected site is archived, only the site is archived and the rest of the group remains active. After a site is archived, it stops consuming active storage quota and begins consuming Microsoft 365 Archive storage. Changes in storage usage might take time to appear in the SharePoint admin center.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To learn more about archive states, see [Archive states in Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-states?view=o365-worldwide).

When a site is archived, compliance features such as eDiscovery and retention labels continue to apply. Site-level and file-level archive states are independent. Archiving a site doesn't change whether individual files were already archived.

1. In the SharePoint admin center, go to [**Active sites**](https://go.microsoft.com/fwlink/?linkid=2185220), and sign in with an account that has [admin permissions](https://learn.microsoft.com/en-us/sharepoint/sharepoint-admin-role) for your organization.
2. In the left column, select one or more sites.
3. Select **Archive**, and to confirm, select **Archive**.
4. Archived sites can be seen on the **Archived sites** page in the SharePoint admin center.

   [![Screenshot of the Archived sites page in the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-archive/archived-sites-page.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/m365-archive/archived-sites-page.png?view=o365-worldwide#lightbox)

   Note

   To archive a hub site, you first need to unregister it as a hub site. Archiving Microsoft Teams-connected sites is only partially supported. For more information, see [Archive a site connected to Teams](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-manage?view=o365-worldwide#archive-a-site-connected-to-teams).

### Archive a site connected to Teams

Sites associated with Teams that use only standard channels are supported for archiving.

Sites associated with Teams that include private or shared channels are only partially supported:

- SharePoint admin center: Archiving a site with channel sites is not possible. \(Message: "The group connected site with channel sites associated can't be archived."\)
- PowerShell and Graph API: Archiving a site with channel sites isn't blocked. Only the main site associated with the Team and its standard channels is archived. Private and shared channel sites remain active. Archiving channel sites directly isn't possible because these sites use unsupported site templates.

## Manage file-level archive

File-level archiving is enabled by default for all SharePoint sites when Microsoft 365 Archive is enabled. Manual file archiving and automatic policy archiving are separate controls. Admins can remove the **Archive** action from users while continuing to use admin-defined policies to archive eligible files automatically.

[SharePoint Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) can control manual file archiving for all SharePoint sites, a subset of sites, or not at all. Admins can also choose whether new sites allow manual file archiving. When manual file archiving is enabled for a site, users with edit permissions can archive files.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To control manual file archiving, admins can use these PowerShell settings.

1. **Tenant-level manual archiving**. To use site archive and automatic file archive policies without showing users the **Archive** action, set the ***-AllowFileArchive*** property of the ***Set-SPOTenant*** cmdlet to False. This tenant setting overrides the site-level property with the same name and blocks manual file archiving across the tenant. Admin-defined policies can still archive eligible files automatically. Site-level archive remains available, and existing archived files can still be reactivated. This flag was introduced into SPO admin PowerShell starting in version 16.0.26714.12000.

   ```PowerShell
   Set-SPOTenant -AllowFileArchive $false
   ```

2. **Site-level manual archiving**. To control which sites show the **Archive** action to users, use the ***-AllowFileArchive*** property of the ***Set-SPOSite*** cmdlet. This flag was introduced into SPO admin PowerShell starting in version 16.0.26211.12000. When set to False, users can't manually archive new files on the site, but existing archived files can still be reactivated.

   ```PowerShell
   Set-SPOSite -Identity <site_url> -AllowFileArchive $false
   ```

3. **Manual archiving defaults for new sites**. To control whether users can manually archive files on sites created in the future, use the ***-AllowFileArchiveOnNewSitesByDefault*** property of the ***Set-SPOTenant*** cmdlet. By default, this property is set to True. Its value is copied to the site's ***-AllowFileArchive*** property when the site is created.

   ```PowerShell
   Set-SPOTenant -AllowFileArchiveOnNewSitesByDefault $false
   ```

Admins can also utilize PowerShell to view usage of file-level archive. [SharePoint Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) or [Global Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) can see how much total storage is consumed by file-level archiving for a given site. The '*ArchivedFileDiskUsed*' property of the ***Get-SPOSite*** cmdlet indicates the storage consumed by all archived files on that site in bytes.

```PowerShell
Get-SPOSite -Identity <site_url>
```

## Audit archive activity

Search the Microsoft 365 audit log for **Archived file** \(`FileArchived`\) to determine whether a user or system account archived a file. When an automatic file archive policy archives a file, the event includes the policy ID, policy version, and the file's last access date. For more information, see [Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities#file-and-page-activities).

## Manage archived sites

Archived sites can be reactivated or deleted. Deletion of archived sites follows the same behavior as that of active sites; that is, a site doesn't need to be reactivated before being deleted. However, sites in the "Reactivating" state can't be deleted until reactivation completes.

Admins can view details of the site, such as the URL, Archive Status, or Storage, from the **Archived sites** page.

## Reactivate a file

When a user needs to regain access to an archived file, they can easily reactivate it in the web version of SharePoint or OneDrive, depending on where the file is hosted. Any user with read access to an archived file is able to reactivate it.

There is no fee for reactivating an archived file. After reactivation, the file can't be archived manually or by policy for 120 days. After the cooldown, an admin-defined policy can archive the file when the policy next evaluates it and the file still meets the policy criteria.

## Reactivate a site

If there's a need to access the site content again, the sites need to be reactivated. The activation time depends on the archive state of the site \("Recently archived" or "Archived"\). For more information, see the [Archive states in Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-states?view=o365-worldwide).

After reactivation, the site moves back to the **Active sites** page. The site resumes its normal function, and the users have the same access rights to the site and its content as they did before the site was archived. After reactivation is complete, the storage consumed by the site will accrue to your storage quota consumption.

1. In the SharePoint admin center, go to [**Active sites**](https://go.microsoft.com/fwlink/?linkid=2185220), and sign in with an account that has [admin permissions](https://learn.microsoft.com/en-us/sharepoint/sharepoint-admin-role) for your organization.

   Note

   If you have Office 365 operated by 21Vianet \(China\), sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=850627), then browse to the SharePoint admin center and open the **Active sites** page.
2. In the left column, select a site that needs to be reactivated.
3. On the command bar, select **Archive**.
4. On the **Archive** pane, select **Reactivate**.
5. If you're trying to reactivate a site from "Archived" state, you see a confirmation pop-up that shows an estimated price for reactivation. Select **Confirm** to reactivate. The site enters the "Reactivating" state. It moves to active sites once reactivation is complete.

[![Screenshot of an example site that you are reactivating in the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/m365-archive/reactivate-site-example.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/m365-archive/reactivate-site-example.png?view=o365-worldwide#lightbox)

When you reactivate a site, its permissions, lists, pages, files, folder-structure, site-level policies, and other metadata will revert to the prearchival state, except if files are deleted from archived sites. The only two exceptions are when files are deleted while the site is archived:

- Content in the recycle bin expires naturally, and that expiration continues while archived.
- Content marked to be deleted by retention policies will still be deleted as normal.

Other than these two exceptions, you can expect the site to be unchanged. Files that were archived at file level before the site was archived remain archived after the site is reactivated and must be reactivated separately.

## Change the archive status of a site via PowerShell

You can archive and reactivate sites by using the PowerShell cmdlet [**Set-SPOSiteArchiveState**](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spositearchivestate).

## Change the archive status of a site via Graph API

You can archive a site by using the Graph API **beta** endpoint [**site: archive**](https://learn.microsoft.com/en-us/graph/api/site-archive) or reactivate it by using the Graph API **beta** endpoint [**site: unarchive**](https://learn.microsoft.com/en-us/graph/api/site-unarchive).

## Site templates supported

| Template ID | Template | Template name |
| --- | --- | --- |
| 1 | Team site \(classic experience\) | STS#0 |
| 1 | Blank Site | STS#1 |
| 1 | Document Workspace | STS#2 |
| 1 | Team site | STS#3 |
| 68 | Communication site | SITEPAGEPUBLISHING#0 |
| 64 | Teams site | GROUP#0 |
| 32 | News site | SPSNEWS#0 |
| 33 | News site | SPSNHOME#0 |
| 4 | Wiki site | WIKI#0 |
| 56 | Enterprise Wiki | ENTERWIKI#0 |
| 7 | Document center | BDR#0 |
| 14483 | Records Center | OFFILE#0 |
| 14483 | Records Center | OFFILE#1 |

Note

OneDrive accounts \(site template 21\) can't be archived by admins. Some accounts will be put into archive by the OneDrive service when they are unlicensed for 93 days or more. When the service archives these accounts, admins can reactivate the accounts via PowerShell. [Learn more about unlicensed OneDrive accounts](https://learn.microsoft.com/en-us/SharePoint/unlicensed-onedrive-accounts).
