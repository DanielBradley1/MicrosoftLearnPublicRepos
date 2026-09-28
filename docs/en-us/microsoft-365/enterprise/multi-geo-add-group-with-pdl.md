<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-add-group-with-pdl?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Create a Microsoft 365 group with a specific preferred data location

When users in a multi-geo environment create a Microsoft 365 group, the group preferred data location \(PDL\) is automatically set to that of the user. Global, SharePoint, and Exchange Administrators can create groups in any *Geography* they select.

If you need to create a group with a specific PDL, you can do that from the [SharePoint admin center](https://go.microsoft.com/fwlink/?linkid=2185219) or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet. When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.

To create a Microsoft 365 group with the PDL that you specify, go to the [SharePoint admin center](https://go.microsoft.com/fwlink/?linkid=2185219) in the *Geography* location where you want to create the group site.

For example, if you want to create a group site in your Australia location, you can go to `https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement`

1. Select **+ Create**.
2. Follow the process to create a group site.

Your group site will be provisioned in the *Geography* location corresponding to the SharePoint admin center from which you initiated the site creation request.

## Using Exchange PowerShell

Connect to Exchange Online PowerShell and pass the parameter *-MailboxRegion* with the geo location code.

For example:

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot of New-UnifiedGroup PowerShell cmdlet with syntax.](https://learn.microsoft.com/en-us/microsoft-365/media/multi-geo-new-group-with-pdl-powershell.png?view=o365-worldwide)

Note

SharePoint group site provisioning is on-demand. The site will be provisioned the first time a group owner or member attempts to access it.

## Geo location codes

| Microsoft 365 Geography | PreferredDataLocation \(PDL\) Value |
| :--- | :--- |
| South Korea, Japan, Singapore, Malaysia, Hong Kong Special Administrative Region | APC |
| Australia | AUS |
| Austria | AUT |
| Brazil | BRA |
| Canada | CAN |
| Chile | CHL |
| Denmark | DNK |
| France, Netherlands, Ireland, Norway, Switzerland, Austria, Finland, Sweden, Germany | EUR |
| France | FRA |
| Germany | DEU |
| India | IND |
| Indonesia | IDN |
| Israel | ISR |
| Italy | ITA |
| Japan | JPN |
| Korea | KOR |
| Malaysia | MYS |
| Mexico | MEX |
| New Zealand | NZL |
| Norway | NOR |
| Poland | POL |
| Qatar | QAT |
| South Africa | ZAF |
| Spain | ESP |
| Sweden | SWE |
| Switzerland | CHE |
| Taiwan | TWN |
| United Arab Emirates | ARE |
| United Kingdom | GBR |
| United States | NAM |

Note

To use a security filter for Italy, New Zealand, Spain, or Sweden in eDiscovery, you must have [premium features in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-settings-general) enabled.

## Related articles

- [Connect to Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell)
- [Create groups with a specific preferred data location using Graph API](https://learn.microsoft.com/en-us/graph/api/group-post-groups)
