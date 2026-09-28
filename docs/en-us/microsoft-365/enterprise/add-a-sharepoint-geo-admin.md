<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/add-a-sharepoint-geo-admin?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-01 -->

# Add or remove a *Geography* administrator in Microsoft 365 Multi-Geo

You can configure separate administrators for each *Geography* location that you have in your *Tenant*. These administrators will have access to the SharePoint and OneDrive settings that are specific to their *Geography* location.

Some services - such as the term store - are administered from the *Primary Provisioned Geography* location and replicated to *Satellite Geography* locations. The *Geography* admin for the *Primary Provisioned Geography* location has access to these, whereas *Geography* admins for *Satellite Geography* locations don't.

Global administrators and SharePoint administrators continue to have access to settings in the *Primary Provisioned Geography* location and all *Satellite Geography* locations.

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Configuring *Geography* administrators

Configuring *Geography* admins requires the SharePoint PowerShell module.

Use [Connect-SPOService](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/connect-sposervice) to connect to the admin center of the *Geography* location where you want to add the *Geography* admin. \(For example, Connect-SPOService https://ContosoEUR-admin.sharepoint.com.\)

To view the existing *Geography* admins of a location, run `Get-SPOGeoAdministrator`

## Adding a user as a *Geography* admin

To add a user as a *Geography* admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

To remove a user as a *Geography* Admin of a location, run `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## Adding a group as a *Geography* admin

You can add a security group or a mail-enabled security group as a *Geography* admin. \(Distribution groups and Microsoft 365 Groups aren't supported.\)

To add a group as a *Geography* administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`

To remove a group as a *Geography* administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Note that not all security groups have a group alias. If you want to add a security group that doesn't have an alias, run [Get-MgGroup](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.groups/get-mggroup) to retrieve a list of groups, find your security group's ObjectID, and then run:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## Related articles

- [Add-SPOGeoAdministrator](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/add-spogeoadministrator)
- [Get-SPOGeoAdministrator](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spogeoadministrator)
- [Remove-SPOGeoAdministrator](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/remove-spogeoadministrator)
- [Set an alias \(MailNickName\) for a security group](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.groups/update-mggroup)
