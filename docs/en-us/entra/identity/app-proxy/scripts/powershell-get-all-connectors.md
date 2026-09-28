<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-connectors -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Get all private network connector groups and connectors in the directory

## Overview

The PowerShell script example lists all Microsoft Entra private network connector groups and connectors in your directory.

If you don't have an [Azure subscription](https://learn.microsoft.com/en-us/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an [Azure free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

Note

We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/en-us/powershell/azure/migrate-from-azurerm-to-az).

This sample requires the [Microsoft Graph Beta PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) 2.10 or newer.

## Sample script

```powershell
# This sample script gets all Microsoft Entra private network connector groups with the included connectors.
#
# Version 1.0
#
# This script requires PowerShell 5.1 (x64) or beyond and one of the following modules:
#
# Microsoft.Graph.Beta ver 2.10 or newer
#
# Before you begin:
#    
#    Required Microsoft Entra role at least Application Administrator or Application Developer 
#    or appropriate custom permissions as documented https://learn.microsoft.com/azure/active-directory/roles/custom-enterprise-app-permissions
#
# 

Import-Module Microsoft.Graph.Beta.Applications

Connect-MgGraph -Scope Directory.Read.All -NoWelcome

Write-Host "Reading Microsoft Entra private network connector groups. This operation might take longer..." -BackgroundColor "Black" -ForegroundColor "Green"

$aadapConnectorGroups= Get-MgBetaOnPremisePublishingProfileConnectorGroup -OnPremisesPublishingProfileId "applicationProxy" -Top 100000 

$countAssignedApps, $CountOfConnectorGroups = 0

foreach ($item in $aadapConnectorGroups) {
   
     If ($item.ConnectorGroupType -eq "applicationProxy") {

     Write-Host "Connector group: " $item.Name, "(Id:" $item.Id ")" -BackgroundColor "Black" -ForegroundColor "White" 
     Write-Host "Region: " $item.Region
     
     Write-Host " "

     $connectors = Get-MgBetaOnPremisePublishingProfileConnectorGroupMember -ConnectorGroupId $item.Id -OnPremisesPublishingProfileId "applicationProxy" 

     $connectors | ft

     " ";

     $CountOfConnectorGroups = $CountOfConnectorGroups + 1

     }
}  

Write-Host ("")
Write-Host ("Number of Microsoft Entra private network connector Groups: $CountOfConnectorGroups")
Write-Host ("")
Write-Host ("Finished.") -BackgroundColor "Black" -ForegroundColor "Green"
Write-Host "To disconnect from Microsoft Graph, please use the Disconnect-MgGraph cmdlet."
```

## Script explanation

| Command | Notes |
| --- | --- |
| [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.authentication/connect-mggraph) | Connects to Microsoft Graph |
| [Get-MgBetaOnPremisePublishingProfileConnectorGroup](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/get-mgbetaonpremisepublishingprofileconnectorgroup) | Gets a connector group |
| [Get-MgBetaOnPremisePublishingProfileConnectorGroupMember](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/get-mgbetaonpremisepublishingprofileconnectorgroupmember) | Gets the members of a connector group |

## Next steps

- [Microsoft Graph PowerShell overview](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview)
- [Microsoft Entra application proxy PowerShell examples](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-powershell-samples)
