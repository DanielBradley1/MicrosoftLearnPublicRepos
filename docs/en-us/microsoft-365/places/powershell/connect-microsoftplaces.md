<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/connect-microsoftplaces -->
<!-- Sitemap-Last-Modified: 2024-11-06 -->

# Connect-MicrosoftPlaces

You can connect to Places PowerShell using modern authentication by running the Connect-MicrosoftPlaces cmdlet. This cmdlet works for accounts with or without multifactor authentication \(MFA\).

## Syntax

```powershell
Connect-MicrosoftPlaces
```

## Description

This command creates a PowerShell connection to enable the use of other MicrosoftPlaces PowerShell commands.

## Parameters

No parameters are exposed for this command. A browser window opens where you enter the identity and authentication credentials.

## Frequently asked questions

### Are there any prerequisites to using this command?

No, but make sure you've downloaded and are using the latest version of [Microsoft PowerShell 7](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows). You should also make sure you're using the latest version of the Microsoft Places PowerShell module. You can force the install of the latest version using:

```powershell
Install-Module -Name MicrosoftPlaces -Force
```

### I receive an error when attempting to run Connect-MicrosoftPlaces

This can happen if you've set up a proxy on your PC, as PowerShell 7 will not automatically use these settings when it tries to connect to the internet. To work around this, you need to manually configure the proxy settings within PowerShell 7. This can be done using commands like `netsh winhttp set proxy`.

### Do I need certain permissions to run Connect-MicrosoftPlaces?

No. Permissions are enforced when running other commands after authentication completes.
