<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-sso -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Using single sign-on with cloud sync

The following document describes how to use single sign-on with cloud sync.

## Steps to enable Single Sign-on

Cloud provisioning works with Single Sign-on \(SSO\). Currently there isn't an option to enable SSO when the agent is installed, however you can use the following steps to enable SSO and use it.

### Step 1: Download and extract Microsoft Entra Connect files

1. First, download the latest version of [Microsoft Entra Connect](https://www.microsoft.com/download/details.aspx?id=47594)
2. Open a command prompt using Administrative privileges and navigate to the msi you downloaded.
3. Run the following command: `msiexec /a C:\filepath\AzureADConnect.msi /qb TARGETDIR=C:\filepath\extractfolder`
4. Change filepath and `extractfolder` to match your file path and the name of your extraction folder. The contents should now be in the extraction folder.

### Step 2: Import the ADSync and Seamless SSO PowerShell modules

Note

Azure AD and MSOnline PowerShell modules are deprecated as of March 30, 2024. To learn more, read the [deprecation update](https://techcommunity.microsoft.com/t5/microsoft-entra-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270). After this date, support for these modules are limited to migration assistance to Microsoft Graph PowerShell SDK and security fixes. The deprecated modules will continue to function through March, 30 2025.

We recommend migrating to [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview) to interact with Microsoft Entra ID \(formerly Azure AD\). For common migration questions, refer to the [Migration FAQ](https://learn.microsoft.com/en-us/powershell/azure/active-directory/migration-faq). *Note:* Versions 1.0.x of MSOnline may experience disruption after June 30, 2024.

1. Download, and install [Azure AD PowerShell](https://learn.microsoft.com/en-us/powershell/azure/active-directory/overview).
2. Ensure that Microsoft Entra Connect Sync is installed on the server where you run these commands. The ADSync module must be loaded from the installed product.
3. Import the ADSync PowerShell module by using this command: `Import-Module "$env:ProgramFiles\Microsoft Azure AD Sync\Bin\ADSync\ADSync.psd1"`.
4. Browse to the `Microsoft Azure Active Directory Connect` folder which should be in the extraction folder from Step 1.
5. Import the Seamless SSO PowerShell module by using this command: `Import-Module .\AzureADSSO.psd1`.

### Step 3: Get the list of Active Directory forests on which Seamless SSO has been enabled

1. Run PowerShell as an administrator. In PowerShell, call `New-AzureADSSOAuthenticationContext`. When prompted, enter the credentials of a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Call `Get-AzureADSSOStatus`. This command provides you with the list of Active Directory forests \(look at the "Domains" list\) on which this feature has been enabled.

### Step 4: Enable Seamless SSO for each Active Directory forest

1. Call `Enable-AzureADSSOForest`. When prompted, enter the domain administrator credentials for the intended Active Directory forest.

   Note

   The domain administrator credentials username must be entered in the SAM account name format \(`contoso\johndoe` or `contoso.com\johndoe`\). We use the domain portion of the username to locate the Domain Controller of the Domain Administrator using DNS.

   Note

   The domain administrator account used must not be a member of the Protected Users group. If so, the operation will fail.
2. Repeat the preceding step for each Active Directory forest where you want to set up the feature.

### Step 5: Enable the feature on your tenant

To turn on the feature on your tenant, call `Enable-AzureADSSO -Enable $true`.

## Next steps

- [What is provisioning?](https://learn.microsoft.com/en-us/entra/identity/hybrid/what-is-provisioning)
- [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
