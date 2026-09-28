<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-assign-group-to-app -->
<!-- Sitemap-Last-Modified: 2026-03-11 -->

# Assign a group to a specific Microsoft Entra application proxy application

## Overview

The PowerShell script example assigns a specific group to a Microsoft Entra application proxy application.

If you don't have an [Azure subscription](https://learn.microsoft.com/en-us/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an [Azure free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

Note

We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/en-us/powershell/azure/migrate-from-azurerm-to-az).

The sample requires the [Microsoft Graph Beta PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) 2.10 or newer.

## Sample script

```powershell
#  This sample script assigns a group to a specific Microsoft Entra application proxy application.
#
#  Tip: You can identify the parameters by using the following PS commands:
#    ServicePrincipalObjectId - Get-MgBetaServicePrincipal -Filter "DisplayName eq '<displayname of the app>'" 
#    GroupObjectId - Get-MgBetaGroup -ConsistencyLevel eventual -Count userCount -Search '"DisplayName:<name of the group>"'"
#
# Version 1.0
#
# This script requires PowerShell 5.1 (x64) or beyond and one of the following modules:
#
# Microsoft.Graph.Beta ver 2.10 or newer
#
# Before you begin:
#    
#    Required Microsoft Entra role at least Application Administrator
#    or appropriate custom permissions as documented https://learn.microsoft.com/azure/active-directory/roles/custom-enterprise-app-permissions
#
# 

param(
[parameter(Mandatory=$true)]
[string] $ServicePrincipalObjectId = "null",
[parameter(Mandatory=$true)]
[string] $GroupObjectId = "null"
)

$servicePrincipalObjectId = $ServicePrincipalObjectId
$groupObjectId = $GroupObjectId

If (($servicePrincipalObjectId -eq "null") -or ($groupObjectId -eq "null")) {

    Write-Host "Parameter is missing." -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "
    Write-Host ".\assign-group-to-app.ps1 -ServicePrincipalObjectId <ObjectId of the Microsoft Entra application proxy application service principal> -UserObjectId <ObjectId of the User>" -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "
    Write-Host "Hints:" -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host "You can easily identify the parameters by using the following PS commands:" -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "
    Write-Host "ServicePrincipalObjectId - Get-MgBetaServicePrincipal -Filter "DisplayName eq '<displayname of the app>'" " -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host "UserObjectId - Get-MgBetaGroup -ConsistencyLevel eventual -Count userCount -Search '"DisplayName:<name of the group>"'" -BackgroundColor "Black" -ForegroundColor "Green"

    Exit
}

Import-Module Microsoft.Graph.Beta.Applications

Connect-MgGraph -Scope Directory.ReadWrite.All -NoWelcome

New-MgBetaGroupAppRoleAssignment -GroupId $groupObjectId -PrincipalId $groupObjectId -ResourceId $servicePrincipalObjectId -AppRoleId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"

Write-Host ("")
Write-Host ("Finished.") -BackgroundColor "Black" -ForegroundColor "Green"
Write-Host ("")
Write-Host "To disconnect from Microsoft Graph, please use the Disconnect-MgGraph cmdlet." 
```

## Script explanation

| Command | Notes |
| --- | --- |
| [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.authentication/connect-mggraph) | Connects to Microsoft Graph |
| [New-MgBetaGroupAppRoleAssignment](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/new-mgbetagroupapproleassignment) | Assigns an app role to a group |

## Next steps

- [Microsoft Graph PowerShell overview](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview)
- [Microsoft Entra application proxy PowerShell examples](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-powershell-samples)
