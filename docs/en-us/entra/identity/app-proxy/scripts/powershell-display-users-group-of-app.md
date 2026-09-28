<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-display-users-group-of-app -->
<!-- Sitemap-Last-Modified: 2026-03-11 -->

# Display users and groups assigned to an application proxy application

## Overview

The PowerShell script example lists the users and groups assigned to a specific Microsoft Entra application proxy application.

If you don't have an [Azure subscription](https://learn.microsoft.com/en-us/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an [Azure free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

Note

We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/en-us/powershell/azure/migrate-from-azurerm-to-az).

The sample requires the [Microsoft Graph Beta PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) 2.10 or newer.

## Sample script

```powershell
# This sample script displays users and groups assigned to the specified Microsoft Entra application proxy application.
#
# .\display-users-group-of-an-app.ps1 -ObjectId <ObjectId of the service principal> (Enterprise App)
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
[string] $ObjectId = "null"
)

$aadapServPrincObjId=$ObjectId

If ($aadapServPrincObjId -eq "null") {

    Write-Host "Parameter is missing." -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "
    Write-Host ".\display-users-group-of-an-app.ps1 -ObjectId <ObjectId of the service principal (Enterprise App)>" -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "

    Exit
}

Import-Module Microsoft.Graph.Beta.Applications

Connect-MgGraph -Scope Directory.Read.All -NoWelcome

Write-Host "Reading users. This operation might take longer..." -BackgroundColor "Black" -ForegroundColor "Green"

$users= Get-MgBetaUser -Top 1000000

Write-Host "Reading groups. This operation might take longer..." -BackgroundColor "Black" -ForegroundColor "Green"

$groups = Get-MgBetaGroup -Top 1000000 

try {$app = Get-MgBetaServicePrincipalById -Id $aadapServPrincObjId}

catch {

    Write-Host "Possibly the ObjetId is incorrect." -BackgroundColor "Black" -ForegroundColor "Red"
    Write-Host " "

    Exit
}

Write-Host ("Application: " + $app.DisplayName + "(ServicePrinc. ObjID:" + $aadapServPrincObjId + ")")
Write-Host ("")
Write-Host ("Assigned (directly and through group membership) users:")
Write-Host ("")

$number=0

foreach ($item in $users) {

   $listOfAssignments = Get-MgBetaUserAppRoleAssignment -UserId $item.Id

   $assigned = $false

   foreach ($item2 in $listOfAssignments) { if ($item2.ResourceId -eq $aadapServPrincObjId) { $assigned = $true } }

     If ($assigned -eq $true) {
        Write-Host ("DisplayName: " + $item.DisplayName + " UPN: " + $item.UserPrincipalName + " ObjectID: " + $item.Id)
        $number = $number + 1
     }
}

Write-Host ("")
Write-Host ("Number of (directly and through group membership) users: " + $number)
Write-Host ("")
Write-Host ("")
Write-Host ("Assigned groups:")
Write-Host ("")

$number=0

foreach ($item in $groups) {

   $listOfAssignments = Get-MgBetaGroupAppRoleAssignment -GroupId $item.Id

   $assigned = $false

   foreach ($item2 in $listOfAssignments) { If ($item2.ResourceID -eq $aadapServPrincObjId) { $assigned = $true } }

   If ($assigned -eq $true) {
        Write-Host ("DisplayName: " + $item.DisplayName + " ObjectID: " + $item.Id)
        $number=$number+1
   }
}

  
Write-Host ("")
Write-Host ("Number of assigned groups: " + $number)
Write-Host ("")

Write-Host ("")
Write-Host ("Finished.") -BackgroundColor "Black" -ForegroundColor "Green"
Write-Host ("") 
Write-Host "To disconnect from Microsoft Graph, please use the Disconnect-MgGraph cmdlet."
```

## Script explanation

| Command | Notes |
| --- | --- |
| [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.authentication/connect-mggraph) | Connects to Microsoft Graph |
| [Get-MgBetaServicePrincipalById](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/get-mgbetaserviceprincipalbyid) | Gets a service principal by ID |
| [Get-MgBetaUser](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.users/get-mgbetauser) | Gets a user |
| [Get-MgBetaGroup](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.groups/get-mgbetagroup) | Gets a group |
| [Get-MgBetaUserAppRoleAssignment](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/get-mgbetagroupapproleassignment) | Gets the application role assignment |

## Next steps

- [Microsoft Graph PowerShell overview](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview)
- [Microsoft Entra application proxy PowerShell examples](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-powershell-samples)
