<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/powershell -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Build PowerShell scripts with Microsoft Graph

This tutorial teaches you how to build a PowerShell script that uses the Microsoft Graph API to access data on behalf of a user.

Note

To learn how to use Microsoft Graph to access data using app-only authentication, see this [app-only authentication tutorial](https://learn.microsoft.com/en-us/graph/tutorials/powershell-app-only).

In this tutorial, you will:

- [Get the signed-in user](https://learn.microsoft.com/en-us/graph/api/user-get)
- [List the user's inbox messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages)
- [Send an email](https://learn.microsoft.com/en-us/graph/api/user-sendmail)

Tip

As an alternative to following this tutorial, you can download the completed code through the [quick start](https://developer.microsoft.com/graph/quick-start?state=option-powershell) tool, which automates app registration and configuration. The downloaded code works without any modifications required.

You can also download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-powershell/tree/main/user-auth) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have [PowerShell](https://learn.microsoft.com/en-us/powershell) installed on your development machine. PowerShell 5.1 is the minimum requirement, but PowerShell 7 is recommended.

You should also have a Microsoft work or school account with an Exchange Online mailbox. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a one-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/microsoft-365/try).

Note

This tutorial was written with PowerShell 7.2.2 and Microsoft Graph PowerShell SDK version 1.9.5. The steps in this guide might work with other versions, but that has not been tested.

## Register an application for user authentication

Register an application that supports [user authentication](https://learn.microsoft.com/en-us/graph/auth-v2-user) using [device code flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code). You can register an application using the Microsoft Entra admin center, or by using the [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/get-started).

- [Microsoft Entra admin center](#tabpanel_1_aad)
- [PowerShell](#tabpanel_1_powershell)

1. Open a browser and navigate to the [Microsoft Entra admin center](https://entra.microsoft.com) and sign in using a Global administrator account.
2. Select **Microsoft Entra ID** in the left-hand navigation, expand **Identity**, expand **Applications**, then select **App registrations**.

   ![A screenshot of the App registrations](https://learn.microsoft.com/en-us/graph/tutorials/images/entra-portal-app-registrations.png)
3. Select **New registration**. Enter a name for your application, for example, `Graph User Auth Tutorial`.
4. Set **Supported account types** as desired. The options are:
   | Option | Who can sign in? |
   | --- | --- |
   | **Accounts in this organizational directory only** | Only users in your Microsoft 365 organization |
   | **Accounts in any organizational directory** | Users in any Microsoft 365 organization \(work or school accounts\) |
   | **Accounts in any organizational directory ... and personal Microsoft accounts** | Users in any Microsoft 365 organization \(work or school accounts\) and personal Microsoft accounts |
5. Leave **Redirect URI** empty.
6. Select **Register**. On the application's **Overview** page, copy the value of the **Application \(client\) ID** and save it. You'll need it in the next step. If you chose **Accounts in this organizational directory only** for **Supported account types**, also copy the **Directory \(tenant\) ID** and save it.

   ![A screenshot of the application ID of the new app registration](https://learn.microsoft.com/en-us/graph/tutorials/images/aad-application-id.png)
7. Select **Authentication** under **Manage**. Locate the **Advanced settings** section and change the **Allow public client flows** toggle to **Yes**, then choose **Save**.

   ![A screenshot of the Allow public client flows toggle](https://learn.microsoft.com/en-us/graph/tutorials/images/aad-default-client-type.png)

To use PowerShell, you need the Microsoft Graph PowerShell SDK. If you don't have it, see [Install the Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) for installation instructions.

Important

The PowerShell script requires a work/school account with the Application administrator, Cloud application administrator, or Global administrator role. If your account has the Application developer role, you can register in the Microsoft Entra admin center.

1. Create a new file named **RegisterAppForUserAuth.ps1** and add the following code.

   ```powershell
   param(
     [Parameter(Mandatory=$true,
     HelpMessage="The friendly name of the app registration")]
     [String]
     $AppName,

     [Parameter(Mandatory=$false,
     HelpMessage="The sign in audience for the app")]
     [ValidateSet("AzureADMyOrg", "AzureADMultipleOrgs", `
     "AzureADandPersonalMicrosoftAccount", "PersonalMicrosoftAccount")]
     [String]
     $SignInAudience = "AzureADandPersonalMicrosoftAccount",

     [Parameter(Mandatory=$false)]
     [Switch]
     $StayConnected = $false
   )

   # Tenant to use in authentication.
   # See https://learn.microsoft.com/azure/active-directory/develop/v2-oauth2-device-code#device-authorization-request
   $authTenant = switch ($SignInAudience)
   {
     "AzureADMyOrg" { "tenantId" }
     "AzureADMultipleOrgs" { "organizations" }
     "AzureADandPersonalMicrosoftAccount" { "common" }
     "PersonalMicrosoftAccount" { "consumers" }
     default { "invalid" }
   }

   if ($authTenant -eq "invalid")
   {
     Write-Host -ForegroundColor Red "Invalid sign in audience:" $SignInAudience
     Exit
   }

   # Requires an admin
   Connect-MgGraph -Scopes "Application.ReadWrite.All User.Read" -UseDeviceAuthentication -ErrorAction Stop

   # Get context for access to tenant ID
   $context = Get-MgContext -ErrorAction Stop

   if ($authTenant -eq "tenantId")
   {
     $authTenant = $context.TenantId
   }

   # Create app registration
   $appRegistration = New-MgApplication -DisplayName $AppName -SignInAudience $SignInAudience `
    -IsFallbackPublicClient -ErrorAction Stop
   Write-Host -ForegroundColor Cyan "App registration created with app ID" $appRegistration.AppId

   # Create corresponding service principal
   if ($SignInAudience -ne "PersonalMicrosoftAccount")
   {
     New-MgServicePrincipal -AppId $appRegistration.AppId -ErrorAction SilentlyContinue `
      -ErrorVariable SPError | Out-Null
     if ($SPError)
     {
       Write-Host -ForegroundColor Red "A service principal for the app could not be created."
       Write-Host -ForegroundColor Red $SPError
       Exit
     }

     Write-Host -ForegroundColor Cyan "Service principal created"
   }

   Write-Host
   Write-Host -ForegroundColor Green "SUCCESS"
   Write-Host -ForegroundColor Cyan -NoNewline "Client ID: "
   Write-Host -ForegroundColor Yellow $appRegistration.AppId
   Write-Host -ForegroundColor Cyan -NoNewline "Auth tenant: "
   Write-Host -ForegroundColor Yellow $authTenant

   if ($StayConnected -eq $false)
   {
     Disconnect-MgGraph | Out-Null
     Write-Host "Disconnected from Microsoft Graph"
   }
   else
   {
     Write-Host
     Write-Host -ForegroundColor Yellow `
      "The connection to Microsoft Graph is still active. To disconnect, use Disconnect-MgGraph"
   }
   ```

2. Save the file.
3. Open PowerShell and change the current directory to the location of **RegisterAppForUserAuth.ps1**.
4. Run the following command, replacing *<audience-value>* with the desired value \(see the following table\).

   ```powershell
   .\RegisterAppForUserAuth.ps1 -AppName "Graph User Auth Tutorial" -SignInAudience <audience-value>
   ```

   | SignInAudience value | Who can sign in? |
   | --- | --- |
   | `AzureADMyOrg` | Only users in your Microsoft 365 organization |
   | `AzureADMultipleOrgs` | Users in any Microsoft 365 organization \(work or school accounts\) |
   | `AzureADandPersonalMicrosoftAccount` | Users in any Microsoft 365 organization \(work or school accounts\) and personal Microsoft accounts |
   | `PersonalMicrosoftAccount` | Only personal Microsoft accounts |
5. Follow the prompt to open `https://microsoft.com/devicelogin` in a browser, enter the provided code, and complete the authentication process.
6. Copy the **Client ID** and **Auth tenant** values from the script output. You'll need these values in the next step.

   ```powershell
   SUCCESS
   Client ID: 2fb1652f-a9a0-4db9-b220-b224b8d9d38b
   Auth tenant: common
   ```

Note

Notice that you didn't configure any Microsoft Graph permissions on the app registration. The sample uses [dynamic consent](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent#incremental-and-dynamic-user-consent) to request specific permissions for user authentication.

Note

Registering an application for user authentication for the Microsoft Graph PowerShell SDK is optional. The SDK has it's own application registration and corresponding client ID. However, using your own application ID allows for greater control over permission scopes for a particular PowerShell script.

## Authenticate the user

The Microsoft Graph PowerShell SDK provides two authentication methods for user authentication: interactive browser and device code authentication. Interactive browser authentication uses a device's default browser to allow the user to sign in. Device code authentication allows authentication in environments that do not have a default browser. In this exercise you will use device code authentication.

Important

If you do not already have the Microsoft Graph PowerShell SDK installed, [install it now](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) before proceeding.

1. Open PowerShell and use the following command to set the `$clientID` session variable, replacing *<your-client-id>* with the client ID of your app registration.

   ```powershell
   $clientId = <your-client-id>
   ```

2. Set the `$tenantId` session variable. If you chose the option to only allow users in your organization to sign in when registering your application, replace *<tenant-id>* with your organization's tenant ID. Otherwise, replace with `common`.

   ```powershell
   $tenantId = <tenant-id>
   ```

3. Set the `$graphScopes` session variable.

   ```powershell
   $graphScopes = "user.read mail.read mail.send"
   ```

4. Use the following command to authenticate the user inside the current PowerShell session.

   ```powershell
   # Authenticate the user
   Connect-MgGraph -ClientId $clientId -TenantId $tenantId -Scopes $graphScopes -UseDeviceAuthentication
   ```


   Tip


   If you would prefer to use interactive browser authentication, omit the `-UseDeviceAuthentication` parameter.

5. Open a browser and browse to the URL displayed. Enter the provided code and sign in.

   Important

   Be mindful of any existing Microsoft 365 accounts that are logged into your browser when browsing to `https://microsoft.com/devicelogin`. Use browser features such as profiles, guest mode, or private mode to ensure that you authenticate as the account you intend to use for testing.
6. Once completed, return to the PowerShell window. Run the following command to verify the authenticated context.

   ```powershell
   # Get the Graph context
   Get-MgContext
   ```


   ```powershell
   ClientId              : 2fb1652f-a9a0-4db9-b220-b224b8d9d38b
   TenantId              : 601faea3-be45-4960-898f-92b379b17cd9
   CertificateThumbprint :
   Scopes                : {Mail.Read, Mail.Send, openid, profile…}
   AuthType              : Delegated
   AuthProviderType      : DeviceCodeProvider
   CertificateName       :
   Account               : MeganB@contoso.com
   AppName               : PowerShell Graph Tutorial
   ContextScope          : CurrentUser
   Certificate           :
   PSHostVersion         : 2022.4.1
   ClientTimeout         : 00:05:00
   ```

## Get the authenticated user

In this section you will get the authenticated user.

1. In your authenticated PowerShell session, run the following command to get the current context. The context provides information to identify the authenticated user.

   ```powershell
   $context = Get-MgContext
   ```

2. Run the following command to get the user from Microsoft Graph.

   ```powershell
   # Get the authenticated user by UPN
   $user = Get-MgUser -UserId $context.Account -Select 'displayName, id, mail, userPrincipalName'
   ```


   Tip


   You can add the `-Debug` switch to the previous command to see the API request and response.

3. Run the following commands to output user information.

   ```powershell
   Write-Host "Hello," $user.DisplayName
   # For Work/school accounts, email is in Mail property
   # Personal accounts, email is in UserPrincipalName
   Write-Host "Email:", ($user.Mail ?? $user.UserPrincipalName)
   ```


   ```powershell
   Hello, Megan Bowen!
   Email: MeganB@contoso.com
   ```

### Code explained

Consider the command used to get the authenticated user. It's a seemingly simple command, but there are some key details to notice.

#### Accessing 'me'

The `Get-MgUser` command builds a request to the [Get user](https://learn.microsoft.com/en-us/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

The Microsoft Graph PowerShell SDK does not support the `GET /me` API endpoint. In order to use the `GEt /users/{user-id}` endpoint, we must provide a value for the `{user-id}` parameter. In the example above, the `$context.Account` value is used. This value contains the authenticated user's user principal name \(UPN\).

#### Requesting specific properties

The function uses the `-Select` parameter on the command to specify the set of properties it needs. This adds the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) to the API call.

#### Strongly-typed return type

The function returns a `MicrosoftGraphUser` object deserialized from the JSON response from the API. Because the command uses `-Select`, only the requested properties will have values in the returned object. All other properties will have default values.

## Next step

[Read and send email](https://learn.microsoft.com/en-us/graph/tutorials/powershell-email)
