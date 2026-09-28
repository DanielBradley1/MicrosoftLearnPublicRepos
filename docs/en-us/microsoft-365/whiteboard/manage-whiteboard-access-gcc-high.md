<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-gcc-high?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-10-20 -->

# Manage access to Microsoft Whiteboard for GCC High environments

Note

This guidance applies to US Government Community Cloud \(GCC\) High environments.

Microsoft Whiteboard on OneDrive for Business is enabled by default for applicable Microsoft 365 tenants. It can be enabled or disabled at a tenant-wide level. You should also ensure that **Microsoft Whiteboard Services** is enabled in the **Microsoft Entra admin center** > **Enterprise applications**.

The following URLs are required:

- 'https://\*.office365.us/'
- 'https://login.microsoftonline.us/'
- 'https://graph.microsoft.us/'
- 'https://graph.microsoftazure.us/'
- 'https://admin.onedrive.us'
- 'https://shell.cdn.office.net/'
- 'https://config.ecs.gov.teams.microsoft.us'
- 'https://tb.events.data.microsoft.com/'

You can control access to Whiteboard in the following ways:

- Enable or disable Whiteboard for your entire tenant using the [SharePoint Online PowerShell module](https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell).
- Show or hide Whiteboard for specific users in meetings using a Teams meeting policy. It will still be visible via the web, native clients, and the Teams tab app.
- Require conditional access policies for accessing Whiteboard using the Microsoft Entra admin center.

Note

Whiteboard on OneDrive for Business doesn't appear in the Microsoft 365 admin center. Teams meeting policy only hides Whiteboard entry points, it doesn't prevent users from using Whiteboard. Conditional access policies prevent access to Whiteboard, but doesn't hide the entry points.

## Enable or disable Whiteboard

To enable or disable Whiteboard for your tenant, do the following steps:

1. Use the [SharePoint Online PowerShell module](https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell) to enable or disable all Fluid Experiences across your Microsoft 365 tenant.
2. Connect to [SharePoint Online PowerShell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).
3. Enable Fluid using the following `Set-SPOTenant` cmdlet:

   ```powershell
   Set-SPOTenant -IsWBFluidEnabled $true
   ```

The change should take approximately 60 minutes to apply across your tenancy. If you don't see this option, you'll need to update the module.

Note

By default, Whiteboard is enabled. If it has been disabled in the Microsoft Entra enterprise applications, then Whiteboard on OneDrive for Business will not work.

## Show or hide Whiteboard

To show or hide Whiteboard in meetings, see [Meeting policy settings](https://learn.microsoft.com/en-us/microsoftteams/meeting-policies-content-sharing).

## See also

[Manage data for Whiteboard - GCC High](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-data-gcc-high?view=o365-worldwide)

[Manage sharing for Whiteboard - GCC High](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-sharing-gcc-high?view=o365-worldwide)

[Manage clients for Whiteboard - GCC High](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-clients-gcc-high?view=o365-worldwide)
