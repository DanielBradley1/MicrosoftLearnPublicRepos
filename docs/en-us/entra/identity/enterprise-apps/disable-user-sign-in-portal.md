<!-- Source: https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/disable-user-sign-in-portal -->
<!-- Sitemap-Last-Modified: 2025-12-12 -->

# Disable user sign-in for an application

There might be situations while configuring or managing an application where you don't want tokens to be issued for an application. Or, you might want to block an application that you don't want your employees to try to access. To block user access to an application, you can disable user sign-in for the application, which prevents all tokens from being issued for that application.

In this article, you learn how to prevent users from signing in to an application in Microsoft Entra ID through both the Microsoft Entra admin center and PowerShell. If you're looking for how to block specific users from accessing an application, use [user or group assignment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

Note

The steps in this article disable user sign-in for a single tenant. If you need to globally disable an application across all tenants \(for multitenant apps\), consider [deactivating the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/deactivate-application-portal) instead, which prevents all token issuance globally.

## Prerequisites

To disable user sign-in, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - Cloud Application Administrator
  - Application Administrator
  - owner of the service principal

## Disable user sign-in using the Microsoft Entra admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **All applications**.
3. Search for the application you want to disable a user from signing in, and select the application.
4. Select **Properties**.
5. Select **No** for **Enabled for users to sign-in?**.
6. Select **Save**.

## Disable user sign-in using Microsoft Entra PowerShell

You might know the AppId of an app that doesn't appear on the Enterprise apps list. For example, if you delete the app or the service principal isn't yet created because Microsoft preauthorizes it. You can manually create the service principal for the app and then disable it by using the following Microsoft Entra PowerShell cmdlet.

Ensure you install the Microsoft Entra PowerShell module. In case you're prompted to install a NuGet module or the new Microsoft Entra PowerShell V2 module, type Y and press ENTER. You need to sign in as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).

```PowerShell
# Connect to Microsoft Entra PowerShell
Connect-Entra -scopes "Application.ReadWrite.All"

# The AppId of the service principal to be disabled
$appId = "{AppId}"

# Disable the service principal
$servicePrincipal = Get-EntraServicePrincipal -Filter "appId eq '$appId'"
Set-EntraServicePrincipal -ObjectId $servicePrincipal.ObjectId -AccountEnabled $false
```

## Disable user sign-in using Microsoft Graph PowerShell

You might know the AppId of an app that doesn't appear on the Enterprise apps list. For example, if you delete the app or the service principal isn't yet created due to the app because Microsoft preauthorizes it. You can manually create the service principal for the app and then disable it by using the following Microsoft Graph PowerShell cmdlet.

Ensure you install the Microsoft Graph module \(use the command `Install-Module Microsoft.Graph`\). You need to sign in as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).

```powershell
# Connect to Microsoft Graph PowerShell
Connect-MgGraph -Scopes "Application.ReadWrite.All"

# Get the AppId of the service principal to be disabled  
$appId = "{AppId}"  
$servicePrincipal = Get-MgServicePrincipal -Filter "appId eq '$appId'"  

# Disable the service principal
Update-MgServicePrincipal -ServicePrincipalId $servicePrincipal.Id -AccountEnabled:$false 
```

## Disable user sign-in using Microsoft Graph API

You might know the AppId of an app that doesn't appear on the Enterprise apps list. For example, if you delete the app or the service principal isn't yet created due to the app because Microsoft preauthorizes it. You can manually create the service principal for the app and then disable it by using the following Microsoft Graph call.

To disable sign-in to an application, sign in to [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).

You need to consent to the `Application.ReadWrite.All` permission.

Run the following query to disable user sign-in to an application.

```http
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/00001111-aaaa-2222-bbbb-3333cccc4444

Content-type: application/json

{
    "accountEnabled": false
}
```

## Related content

- [Remove a user or group assignment from an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)
