<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-grant-access -->
<!-- Sitemap-Last-Modified: 2025-07-24 -->

# Grant access to the inbound provisioning API

## Introduction

After you've configured [API-driven inbound provisioning app](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-configure-app), you need to grant access permissions so that API clients can send requests to the provisioning [/bulkUpload](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-post-bulkupload) API and query the [provisioning logs API](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary). This tutorial walks you through the steps to configure these permissions.

Depending on how your API client authenticates with Microsoft Entra ID, you can select between two configuration options:

- [Configure a service principal](#configure-a-service-principal): Follow these instructions if your API client plans to use a service principal of a [Microsoft Entra registered app](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal) and authenticate using OAuth client credentials grant flow.
- [Configure a managed identity](#configure-a-managed-identity): Follow these instructions if your API client plans to use a Microsoft Entra [managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

## Configure a service principal

This configuration registers an app in Microsoft Entra ID that represents the external API client and grants it permission to invoke the inbound provisioning API. The service principal client ID and client secret can be used in the OAuth client credentials grant flow.

1. Log in to Microsoft Entra admin center \([https://entra.microsoft.com](https://entra.microsoft.com)\) with at least [Application Administrator](https://go.microsoft.com/fwlink/?linkid=2247823) login credentials.
2. Browse to **Entra ID** > **App registrations**.
3. Click on the option **New registration**.
4. Provide an app name, select the default options, and click on **Register**.

   [![Screenshot of app registration.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/register-app.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/register-app.png#lightbox)

5. Copy the **Application \(client\) ID** and **Directory \(tenant\) ID** values from the Overview blade and save it for later use in your API client.

   [![Screenshot of app client ID.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/app-client-id.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/app-client-id.png#lightbox)

6. In the context menu of the app, select **Certificates & secrets** option.
7. Create a new client secret. Provide a description for the secret and expiry date.
8. Copy the generated value of the client secret and save it for later use in your API client.
9. From the context menu **API permissions**, select the option **Add a permission**.
10. Under **Request API permissions**, select **Microsoft Graph**.
11. Select **Application permissions**.
12. Search and select permissions **ProvisioningLog.Read.All** and **SynchronizationData-User.Upload**.

    Note

    If you're configuring the service principal for use by an HR ISV that will instantiate the API-driven provisioning app in your tenant, consider granting the `Application.ReadWrite.OwnedBy` and `SynchronizationData-User.Upload.OwnedBy` application permissions. This ensures that the ISV can only upload data to the `/bulkUpload` API endpoint associated with the app it creates.
13. Click on **Grant admin consent** on the next screen to complete the permission assignment. Click Yes on the confirmation dialog. Your app should have the following permission sets.

    [![Screenshot of app permissions.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/api-client-permissions.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/api-client-permissions.png#lightbox)

14. You're now ready to use the service principal with your API client.
15. For production workloads, we recommend using [client certificate-based authentication](https://learn.microsoft.com/en-us/entra/identity-platform/howto-authenticate-service-principal-powershell) with the service principal or managed identities.

## Configure a managed identity

This section describes how you can assign the necessary permissions to a managed identity.

1. Configure a [managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview) for use with your Azure resource.
2. Copy the name of your managed identity from the Microsoft Entra admin center. For example: The screenshot below shows the name of a system assigned managed identity associated with an Azure Logic Apps workflow called "CSV2SCIMBulkUpload".

   [![Screenshot of managed identity name.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/managed-identity-name.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/managed-identity-name.png#lightbox)

3. Run the following PowerShell script to assign permissions to your managed identity.

   ```powershell
   Install-Module Microsoft.Graph -Scope CurrentUser

   Connect-MgGraph -Scopes "Application.Read.All","AppRoleAssignment.ReadWrite.All,RoleManagement.ReadWrite.Directory"
   $graphApp = Get-MgServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'"

   $PermissionName = "SynchronizationData-User.Upload"
   $AppRole = $graphApp.AppRoles | `
   Where-Object {$_.Value -eq $PermissionName -and $_.AllowedMemberTypes -contains "Application"}
   $managedID = Get-MgServicePrincipal -Filter "DisplayName eq 'CSV2SCIMBulkUpload'"
   New-MgServicePrincipalAppRoleAssignment -PrincipalId $managedID.Id -ServicePrincipalId $managedID.Id -ResourceId $graphApp.Id -AppRoleId $AppRole.Id

   $PermissionName = "ProvisioningLog.Read.All"
   $AppRole = $graphApp.AppRoles | `
   Where-Object {$_.Value -eq $PermissionName -and $_.AllowedMemberTypes -contains "Application"}
   $managedID = Get-MgServicePrincipal -Filter "DisplayName eq 'CSV2SCIMBulkUpload'"
   New-MgServicePrincipalAppRoleAssignment -PrincipalId $managedID.Id -ServicePrincipalId $managedID.Id -ResourceId $graphApp.Id -AppRoleId $AppRole.Id
   ```

4. To confirm that the permission was applied, find the managed identity service principal under **Enterprise Applications** in Microsoft Entra ID. Remove the **Application type** filter to see all service principals. [![Screenshot of managed identity principal.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/managed-identity-principal.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/managed-identity-principal.png#lightbox)
5. Click on the **Permissions** blade under **Security**. Ensure the permission is set. [![Screenshot of managed identity permissions.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/managed-identity-permissions.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-grant-access/managed-identity-permissions.png#lightbox)
6. You're now ready to use the managed identity with your API client.

## Next steps

- [Quick start using cURL](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-curl-tutorial)
- [Quick start using Graph Explorer](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-graph-explorer)
- [Frequently asked questions about API-driven inbound provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-faqs)
