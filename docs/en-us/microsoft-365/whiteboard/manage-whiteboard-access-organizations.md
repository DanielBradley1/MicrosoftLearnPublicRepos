<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-organizations?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-02-17 -->

# Manage access to Microsoft Whiteboard for your organization

Note

This article applies to Enterprise or Education organizations who use Whiteboard. For US Government GCC High environments, see [Manage access to Microsoft Whiteboard for GCC High environments](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-gcc-high?view=o365-worldwide).

Microsoft Whiteboard is a visual collaboration canvas where people, content, and ideas come together. Microsoft Whiteboard on OneDrive for Business is enabled by default for applicable Microsoft 365 tenants. It can be enabled or disabled at a tenant-wide level. You should also ensure that **Microsoft Whiteboard Services** is enabled in the **Microsoft Entra admin center** > **Enterprise applications**.

Whiteboard conforms to global standards including SOC 1, SOC 2, ISO 27001, HIPAA, and EU Model Clauses.

The following admin settings are required for Whiteboard:

- Whiteboard must be enabled globally in the Microsoft 365 admin center.
- The `Set-SPOTenant -IsWBFluidEnabled` cmdlet must be enabled using [SharePoint Online PowerShell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

You can control access to Whiteboard in the following ways:

- Enable or disable Whiteboard for your entire tenant using the Microsoft 365 admin center.
- Show or hide Whiteboard for specific users in meetings using a Teams meeting policy. It will still be visible via the web, native clients, and the Teams tab app.
- Require conditional access policies for accessing Whiteboard using the Microsoft Entra admin center.

Note

Teams meeting policies only hide Whiteboard entry points; they don't prevent the users from using Whiteboard. Conditional access policies prevent any access to Whiteboard, but don't hide the entry points.

## Enable or disable Whiteboard

To enable or disable Whiteboard for your tenant, do the following steps:

1. Go to the Microsoft 365 admin center.
2. On the home page of the admin center, in the Search box on the top right, type *Whiteboard*.
3. In the search results, select **Whiteboard settings**.
4. On the Whiteboard panel, toggle **Turn Whiteboard on or off for your entire organization** to **On**.
5. Select **Save**.
6. Connect to [SharePoint Online PowerShell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).
7. Enable Fluid using the following `Set-SPOTenant` cmdlet:

   ```powershell
   Set-SPOTenant -IsWBFluidEnabled $true
   ```

## Show or hide Whiteboard

To show or hide Whiteboard in meetings, see [Meeting policy settings](https://learn.microsoft.com/en-us/microsoftteams/meeting-policies-content-sharing). To control the availability of the Whiteboard app for each user within the organization, see [App policy settings](https://learn.microsoft.com/en-us/microsoftteams/app-policies).

## Prevent access to Whiteboard

To prevent access to Whiteboard for specific users, see [Building a Conditional Access policy](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-policies).

## See also

[Manage data for Whiteboard](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-data-organizations?view=o365-worldwide)

[Manage sharing for Whiteboard](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-sharing-organizations?view=o365-worldwide)

[Deploy Whiteboard on Windows](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/deploy-on-windows-organizations?view=o365-worldwide)
