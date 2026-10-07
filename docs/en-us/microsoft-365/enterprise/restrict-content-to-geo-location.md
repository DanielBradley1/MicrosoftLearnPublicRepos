<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/restrict-content-to-geo-location?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-05-09 -->

# Restrict SharePoint site content to a geo location

Under certain circumstances you may choose to enforce a site and its file content to remain in the *Geography* location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another *Geography* location.

You can do this task by using the [Set-SPOSite](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-sposite) cmdlet with the **RestrictedToGeo** parameter. This parameter has a default value of NULL, but you can change it to one of the following restrictions:

| Restriction | Description |
| :--- | :--- |
| NoRestriction | The site can be moved to another *Geography* location. |
| BlockMoveOnly | Site can't be moved to another *Geography* location, but site content can be cached in other *Geography* locations. |
| BlockFull | Site can't be moved to another *Geography* location, and full file content isn't cached in other *Geography* locations. Files' title \(harvested from the content\), file name, and other properties of the file can still be cached in other *Geography* locations.  <br>Content stored in the site before it was configured to BlockFull, may continue to be cached in other *Geography* locations. |

Use the following syntax:

```powershell
Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>
```

For example:

```powershell
Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull
```
