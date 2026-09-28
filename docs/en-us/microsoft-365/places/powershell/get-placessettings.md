<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placessettings -->
<!-- Sitemap-Last-Modified: 2024-11-01 -->

# Get-PlacesSettings

You can use Get-PlacesSettings to view all Microsoft Places features settings configured on your tenant.

Tip

Make sure to launch PowerShell7 as an administrator and connect to the Microsoft Places using Connect-MicrosoftPlaces.

Caution

You might find additional features in the response, but those aren't currently supported. Please refer to [Set-PlacesSettings feature parameters section](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings#feature-parameters) for detailed description for each feature.

## Syntax

```powershell
Get-PlacesSettings 
 [-ReadFromPrimary]
```

## Description

You need to be assigned permissions before you can run this cmdlet. You must have either the Exchange Admin role or the Places TenantPlacesManagement role.

## Examples

**Example 1**

This example returns the up-to-date Places features configured on your tenant.

```powershell
Get-PlacesSettings -ReadFromPrimary 
```

### Parameters

#### -ReadFromPrimary

The ReadFromPrimary parameter dictates that Places feature setting should be retrieved from the primary storage rather than the cache. In the absence of this parameter, your data will be fetched from the cache storage, which might not reflect the most current information.

| Attribute | Description |
| --- | --- |
| Type: | SwitchParameter |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

## Troubleshooting

#### Are there any prerequisites to using this command?

- Ensure that you're running the latest version of [Microsoft PowerShell 7](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows).
- Ensure that you're running the latest version of the Places PowerShell client. You can force the install of the latest version using:

```powershell
Install-Module -Name MicrosoftPlaces -Force
```
