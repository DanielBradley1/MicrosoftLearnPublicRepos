<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-custom-domain-replace-cert -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Get all Microsoft Entra application proxy applications published with the identical certificate and replace it

## Overview

The PowerShell script example replaces the certificates in bulk for all Microsoft Entra application proxy applications published with identical certificate.

If you don't have an [Azure subscription](https://learn.microsoft.com/en-us/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an [Azure free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

Note

We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/en-us/powershell/azure/migrate-from-azurerm-to-az).

The sample requires the [Microsoft Graph Beta PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) 2.10 or newer.

## Sample script

```powershell
# This sample script gets all Microsoft Entra application proxy applications published with the identical certificate.
#
# .\replace_with_the_script_name.ps1 -CurrentThumbprint <thumbprint of the current certificate> -PFXFilePath <full path with PFX filename>
#
# Version 1.0
#
# This script requires PowerShell 5.1 (x64) and one of the following modules:
#
# Microsoft.Graph ver 2.10 or newer
#
# Before you begin:
#    
#    Required Microsoft Entra role at least Application Administrator or Application Developer 
#    or appropriate custom permissions as documented https://learn.microsoft.com/azure/active-directory/roles/custom-enterprise-app-permissions
#
# 

param(
[parameter(Mandatory=$true)]
[string] $CurrentThumbprint = "null",
[parameter(Mandatory=$true)]
[string] $PFXFilePath = "null"
)

$certThumbprint = $CurrentThumbprint
$certPfxFilePath = $PFXFilePath

If (($certThumbprint -eq "null") -or ($certPfxFilePath -eq "null")) {

    Write-Host "Parameter is missing." -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "
    Write-Host ".\get-custom-domain-replace-cert.ps1 -CurrentThumbprint <thumbprint of the current certificate> -PFXFilePath <full path with PFX filename>" -BackgroundColor "Black" -ForegroundColor "Green"
    Write-Host " "

    Exit
}

If ((Test-Path -Path $certPfxFilePath) -eq $False) {

    Write-Host "The pfx file does not exist." -BackgroundColor "Black" -ForegroundColor "Red"
    Write-Host " "

    Exit
}

$securePassword = Read-Host -AsSecureString // please provide the password of the pfx file

Import-Module Microsoft.Graph.Beta.Applications

Connect-MgGraph -Scope Directory.ReadWrite.All -NoWelcome

Write-Host "Reading service principals. This operation might take longer..." -BackgroundColor "Black" -ForegroundColor "Green"

$allApps = Get-MgBetaServicePrincipal -Top 100000 | where-object {$_.Tags -Contains "WindowsAzureActiveDirectoryOnPremApp"}

$numberofAadapApps = 0

Write-Host ("")
Write-Host ("SSL certificate change for the Microsoft Entra application proxy apps below:")
Write-Host ("")

foreach ($item in $allApps) {

  $aadapApp, $aadapAppConf, $aadapAppConf1 = $null, $null, $null


  $aadapAppId =  Get-MgBetaApplication -Filter "AppId eq '$($item.AppID)'"

  $aadapAppConf = Get-MgBetaApplication -ApplicationId $aadapAppId.Id -ErrorAction SilentlyContinue -select OnPremisesPublishing | select OnPremisesPublishing -expand OnPremisesPublishing 
  $aadapAppConf1 = Get-MgBetaApplication -ApplicationId $aadapAppId.Id -ErrorAction SilentlyContinue -select OnPremisesPublishing | select OnPremisesPublishing -expand OnPremisesPublishing `
    | select verifiedCustomDomainCertificatesMetadata -expand verifiedCustomDomainCertificatesMetadata 

  if ($aadapAppConf -ne $null) {

    if ($aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.Thumbprint -match $certThumbprint) {

      Write-Host $item.DisplayName"(AppId: " $item.AppId ", ObjId:" $item.Id")" -BackgroundColor "Black" -ForegroundColor "White"
      Write-Host
      Write-Host "External Url: " $aadapAppConf.ExternalUrl
      Write-Host "Internal Url: " $aadapAppConf.InternalUrl
      Write-Host "Pre-authentication: " $aadapAppConf.ExternalAuthenticationType
      Write-Host

      $params = @{
         onPremisesPublishing = @{
            verifiedCustomDomainKeyCredential = @{
                type="X509CertAndPassword";
                value = [convert]::ToBase64String([System.IO.File]::ReadAllBytes($certPfxFilePath));
            };
            verifiedCustomDomainPasswordCredential = @{
                value = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto([System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($securePassword)) };
         }
      }

      Update-MgBetaApplication -ApplicationId $aadapAppId.Id -BodyParameter $params
  
      $numberofAadapApps = $numberofAadapApps + 1
    }
  }
}

Write-Host
Write-Host "Number of the updated Microsoft Entra application proxy applications: " $numberofAadapApps -BackgroundColor "Black" -ForegroundColor "White"
Write-Host ("")

Write-Host
Write-Host "Finished." -BackgroundColor "Black" -ForegroundColor "Green"
Write-Host "To disconnect from Microsoft Graph, please use the Disconnect-MgGraph cmdlet."
```

## Script explanation

| Command | Notes |
| --- | --- |
| [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.authentication/connect-mggraph) | Connects to Microsoft Graph |
| [Get-MgBetaServicePrincipal](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.applications/get-mgserviceprincipal) | Gets a service principal |
| [Get-MgBetaApplication](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/get-mgbetaapplication) | Gets an Enterprise Application |
| [Update-MgBetaApplication](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.beta.applications/update-mgbetaapplication) | updates an application |

## Next steps

- [Microsoft Graph PowerShell overview](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview)
- [Microsoft Entra application proxy PowerShell examples](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-powershell-samples)
