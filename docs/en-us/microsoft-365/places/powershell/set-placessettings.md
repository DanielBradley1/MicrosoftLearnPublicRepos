<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# Set-PlacesSettings

You can use `Set-PlacesSettings` to turn Microsoft Places features on or off, for your tenant or for a subset of users in your tenant.

Make sure to launch PowerShell7 as an Administrator, and connect to the Microsoft Places node using `Connect-MicrosoftPlaces`.

The rest of this document focuses on two sets of parameters within the Set-PlacesSettings cmdlet:

1. **Feature Parameters**: Utilized to selecting the features available in your tenant.
2. **Scope Parameters**: Utilized to identify the users that have access to the features made available in your tenant.

## Syntax

### Feature

```powershell
Set-PlacesSettings
 [-EnableBuildings]
 [-EnablePlacesWebApp] 
 [-PlacesFinderEnabled]
 [-SpaceAnalyticsEnabled]
```

### Scope

```powershell
Set-PlacesSettings
 [-<Feature Parameter>]
   ['Default:True']
   ['Default:False']
   ['Default:[scope value],OID:[OID]@[TID]:[scope value]']
```

Caution

The Set-PlacesSettings might list additional parameters via Get-Help that are not covered in this article. These parameters are not supported.  
For example, \[-PlacesEnabled\] is no longer supported, and running a command like `Set-PlacesSettings -PlacesEnabled 'Default:true'` will return an error.

Note

It can take up to 12 hours for settings changes to propagate and take effect across your tenant.

## Feature Parameters

### -EnableBuildings

This parameter controls whether users can see buildings in Work plans, Workplace presence, Places finder, and other parts of the Microsoft Places experience.

Starting August 1, 2026, this is ON by default for newly onboarded tenants. For all other tenants, this setting is OFF by default. When this setting is on, it only has an effect if you've [configured buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors).

When this setting is on, users can set their work location to a specific building and filter by building in Places Finder. When off, users can only set their location to "in office" or "remote" and they won't be able to use Places finder.

Tip

This setting allows you to control whether users in your organization can set their work plan to a specific building. There’s a different setting to control whether users can make their work location *visible to other users*. To learn more, please review the documentation for [mailbox calendar configuration](https://learn.microsoft.com/en-us/powershell/module/exchange/set-mailboxcalendarconfiguration).

### -EnablePlacesWebApp

This parameter controls whether users can access the Places app, on the web or inside Outlook, Teams and in Microsoft 365 app.

By default, this is ON for all users in your tenant.

### -PlacesFinderEnabled

This parameter controls whether users can access Places finder and book individual desks.

Starting August 1, 2026, this is ON by default for newly onboarded tenants. For existing tenants that already have Room Lists configured, there are no behavior changes and this remains OFF by default, so you can continue to manage the transition from Room finder to Places finder.

For newly onboarded tenants, Places finder is opt-out. To turn it off for everyone in your tenant, run:

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:false'
```

Because we are evaluating deprecation of the Room finder experiences, we highly recommend adopting Places finder to reduce future migration costs.

For existing tenants with Room Lists configured where this is OFF by default, you might want to turn this on \(and thus enable the new Places finder experience\) for a subset of users before enabling it for everyone.

### -SpaceAnalyticsEnabled

This parameter controls whether users have access to Analytics.

By default, this is OFF for all users in your tenant.

We recommend turning this on for admins and real estate and facilities managers, as this gives them access to data-driven insights for effective space management.

You need to enable buildings separately, as described in [Set up space analytics](https://learn.microsoft.com/en-us/microsoft-365/places/places-analytics).

## Scoping Parameters

After reviewing the individual parameters, consider which feature you would like to have control over. In example, if you wanted to control the **Places core features** which can otherwise be enabled by default, you would follow these steps with -EnablePlacesWebApp.

### Enabling a feature for all users

To enable a feature for everyone in your tenant, set the Default value to `True`. Here's an example showing how Places Finder can be enabled:

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:true'
```

### Disable a feature for all users

To disable a feature for everyone in your tenant, set the Default value to `False`. Here's an example showing how Microsoft Places Finder can be disabled:

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:false'
```

### Limit feature access

To limit feature access to a select group of users, the Default value must be set to either True or False. Additionally, an Object ID \(OID\) value must be provided to identify the users that will be either included or excluded from the default value and your Tenant ID \(TID\). The string to be passed for each of the parameters must be one string concatenated by commas in the format `'Default:[scope value] and OID:[OID]@[TID]:[scope value]'`.

Important

If you plan to use a standard security group, your configuration may not work as expected. To ensure proper functionality, the security group must be set as a [mail-enabled security group](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/compare-groups). OID-based scoping is currently supported only for the **-PlacesFinderEnabled** setting.

Here's an example of how Places Finder can be *disabled* for everyone *except* a specific group of users:

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:false,OID:53612aff-a481-41c1-970b-2ca512e6ae53@ef2a97524-022c7-4bab7-8a8c-bc2c4756201c:true'
```

Here's is an example of how Places Finder can be *enabled* for everyone *except* a select group of users:

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:true,OID:53612aff-a481-41c1-970b-2ca512e6ae53@ef2a97524-022c7-4bab7-8a8c-bc2c4756201c:false'
```

Note

A maximum of 20 OIDs can be used when limiting feature access.

## Troubleshooting

### Are there any prerequisites to using this command?

- Ensure that you're running the latest version of [Microsoft PowerShell 7](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows).
- Ensure that you're running the latest version of the Places PowerShell client. You can force the install of the latest version using:

```powershell
Install-Module -Name MicrosoftPlaces -Force
```

### Do I need certain permissions to run Set-PlacesSettings?

Yes. You need to be assigned permissions before you can run this cmdlet. You must have both the Exchange MailRecipients role and the Places TenantPlacesManagement role. For more information permissions, see [License Requirements](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/license-requirements).

### How do I find the OID for a mail-enabled security group?

Through [Microsoft Entra admin center](https://entra.microsoft.com/), extract the ID of the [desired group](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups)

To find the OID of a [security group through Graph](https://learn.microsoft.com/en-us/entra/identity/users/groups-settings-v2-cmdlets) which would also provide the TenantID, run the following command:

```powershell
Install-module Microsoft.Graph.Groups
Connect-MGGraph -Scopes "Group.Readwrite.all"
Get-MgGroup -Filter "DisplayName eq 'Intune Administrators'" | Select-Object -Property ObjectID
```

To find the OID of a mail-enabled security group through Exchange Online run the following:

```powershell
Connect-ExchangeOnline
Get-DistributionGroup '<Security Group Name>' | Select-Object -Property ExternalDirectoryObjectId
```
