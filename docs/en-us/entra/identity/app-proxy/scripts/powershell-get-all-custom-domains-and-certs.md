<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-custom-domains-and-certs -->
<!-- Sitemap-Last-Modified: 2026-03-11 -->

# Get all application proxy apps using custom domains and certificate information

## Overview

The PowerShell script example lists all Microsoft Entra application proxy applications that are using custom domains and lists the certificate information associated with the custom domains.

If you don't have an [Azure subscription](https://learn.microsoft.com/en-us/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an [Azure free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

Note

We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/en-us/powershell/azure/migrate-from-azurerm-to-az).

The sample requires the [Microsoft Graph Beta PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) 2.10 or newer.

## Sample script

```powershell
# This sample script gets all Microsoft Entra application proxy application custom domain applications & uploaded certificates.
#
# Version 1.0
#
# This script requires PowerShell 5.1 (x64) and one of the following modules:
#
# Microsoft.Graph ver 2.10
#
# Before you begin:
#    
#    Required Microsoft Entra role at least Application Administrator or Application Developer 
#    or appropriate custom permissions as documented https://learn.microsoft.com/azure/active-directory/roles/custom-enterprise-app-permissions
#
# 

Import-Module Microsoft.Graph.Beta.Applications

Connect-MgGraph -Scope Directory.Read.All -NoWelcome

Write-Host "Reading service principals. This operation might take longer..." -BackgroundColor "Black" -ForegroundColor "Green"

$allApps = Get-MgBetaServicePrincipal -Top 100000 | where-object {$_.Tags -Contains "WindowsAzureActiveDirectoryOnPremApp"}

$numberofAadapApps, $certsNumber = 0, 0

[string[]]$certs = $null

Write-Host "Displaying all custom domain Microsoft Entra application proxy applications and the uploaded certificates..." -BackgroundColor "Black" -ForegroundColor "Green"
Write-Host " "

foreach ($item in $allApps) {

 $aadapApp, $aadapAppConf, $aadapAppConf1 = $null, $null, $null
 
 $aadapAppId =  Get-MgBetaApplication -Top 100000 | where-object {$_.AppId -eq $item.AppId}
 $aadapAppConf = Get-MgBetaApplication -ApplicationId $aadapAppId.Id -ErrorAction SilentlyContinue -select OnPremisesPublishing | select OnPremisesPublishing -expand OnPremisesPublishing 
 $aadapAppConf1 = Get-MgBetaApplication -ApplicationId $aadapAppId.Id -ErrorAction SilentlyContinue -select OnPremisesPublishing | select OnPremisesPublishing -expand OnPremisesPublishing `
  | select verifiedCustomDomainCertificatesMetadata -expand verifiedCustomDomainCertificatesMetadata 

  if (($aadapAppConf -ne $null) -and ($aadapAppConf.ExternalUrl -notmatch ".msappproxy.net")) {
   
  Write-Host $item.DisplayName"(AppId: " $item.AppId ", ObjId:" $item.Id")" -BackgroundColor "Black" -ForegroundColor "White"
  Write-Host
  Write-Host "External Url: " $aadapAppConf.ExternalUrl
  Write-Host "Internal Url: " $aadapAppConf.InternalUrl
  Write-Host "Pre-authentication: " $aadapAppConf.ExternalAuthenticationType
  Write-Host

  If ($aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.Thumbprint.Length -ne 0) {
       
        Write-Host " "
        Write-Host "SSL Certificate details:"
        Write-Host "Certificate SubjectName: " $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.SubjectName
        Write-Host "Certificate Issuer: " $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.IssuerName
        Write-Host "Certificate Thumbprint: " $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.Thumbprint
        Write-Host "Valid from: " $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.IssueDate
        Write-Host "Valid to: " $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.ExpiryDate
        Write-Host " "

        if ($null -eq ($aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.Thumbprint | ? { $certs -match $_ })) {
        
        
          $certs += " `r`nSSL Certificate details:`r`nCertificate SubjectName: " + $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.SubjectName
          $certs += "Certificate Issuer: " + $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.IssuerName
          $certs += "Certificate Thumbprint: " + $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.Thumbprint
          $certs += "Valid from: " + $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.IssueDate
          $certs += "Valid to: " + $aadapAppConf1.VerifiedCustomDomainCertificatesMetadata.ExpiryDate + "`r`n"

          $certsNumber = $certsNumber + 1
          
        }

  $numberofAadapApps = $numberofAadapApps + 1      
     }
  }
}


Write-Host
Write-Host "Number of the Microsoft Entra application proxy applications with custom domain: " $numberofAadapApps -BackgroundColor "Black" -ForegroundColor "White"
Write-Host ("")
Write-Host ("Number of uploaded certificates: " + $certsNumber) -BackgroundColor "Black" -ForegroundColor "White"
Write-Host ("")
Write-Host ("Used certificates:") -BackgroundColor "Black" -ForegroundColor "White"
Write-Host ("")

$certs 

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

## Next steps

- [Microsoft Graph PowerShell overview](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview)
- [Microsoft Entra application proxy PowerShell examples](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-powershell-samples)
