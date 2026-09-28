<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Build .NET apps with Microsoft Graph and app-only authentication

This tutorial teaches you how to build a .NET console app that uses the Microsoft Graph API to access data using app-only authentication. App-only authentication is a good choice for background services or applications that need to access data for all users in an organization.

Note

To learn how to use Microsoft Graph to access data on behalf of a user, see this [user \(delegated\) authentication tutorial](https://learn.microsoft.com/en-us/graph/tutorials/dotnet).

In this tutorial, you will:

- [List users](https://learn.microsoft.com/en-us/graph/api/user-list)

Tip

As an alternative to following this tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-dotnet/tree/main/app-auth) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have the [.NET SDK](https://dotnet.microsoft.com/download) installed on your development machine.

You should also have a Microsoft work or school account with the Global administrator role. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a one-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/microsoft-365/try).

Note

This tutorial was written with .NET SDK version 7.0.102. The steps in this guide might work with other versions, but that hasn't been tested.

## Register application for app-only authentication

Register an application that supports app-only authentication using [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

- [Microsoft Entra admin center](#tabpanel_1_aad)
- [PowerShell](#tabpanel_1_powershell)

1. Open a browser and navigate to the [Microsoft Entra admin center](https://entra.microsoft.com) and sign in using a Global administrator account.
2. Select **Microsoft Entra ID** in the left-hand navigation, expand **Identity**, expand **Applications**, then select **App registrations**.

   ![A screenshot of the App registrations](https://learn.microsoft.com/en-us/graph/tutorials/images/entra-portal-app-registrations.png)
3. Select **New registration**. Enter a name for your application, for example, `Graph App-Only Auth Tutorial`.
4. Set **Supported account types** to **Accounts in this organizational directory only**.
5. Leave **Redirect URI** empty.
6. Select **Register**. On the application's **Overview** page, copy the value of the **Application \(client\) ID** and **Directory \(tenant\) ID** and save them. You'll need these values in the next step.

   ![A screenshot of the application ID of the new app registration](https://learn.microsoft.com/en-us/graph/tutorials/images/aad-app-only-application-id.png)
7. Select **API permissions** under **Manage**.
8. Remove the default **User.Read** permission under **Configured permissions** by selecting the ellipses \(**...**\) in its row and selecting **Remove permission**.
9. Select **Add a permission**, then **Microsoft Graph**.
10. Select **Application permissions**.
11. Select **User.Read.All**, then select **Add permissions**.
12. Select **Grant admin consent for...**, then select **Yes** to provide admin consent for the selected permission.

    ![A screenshot of the Configured permissions table after granting admin consent](https://learn.microsoft.com/en-us/graph/tutorials/images/aad-configured-permissions.png)
13. Select **Certificates and secrets** under **Manage**, then select **New client secret**.
14. Enter a description, choose a duration, and select **Add**.
15. Copy the secret from the **Value** column, you'll need it in the next steps.

    Important

    This client secret is never shown again, so make sure you copy it now.

To use PowerShell, you need the Microsoft Graph PowerShell SDK. If you don't have it, see [Install the Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) for installation instructions.

1. Create a new file named **RegisterAppForAppOnlyAuth.ps1** and add the following code.

   ```powershell
   param(
     [Parameter(Mandatory=$true,
     HelpMessage="The friendly name of the app registration")]
     [String]
     $AppName,

     [Parameter(Mandatory=$true,
     HelpMessage="The application permission scopes to configure on the app registration")]
     [String[]]
     $GraphScopes,

     [Parameter(Mandatory=$false)]
     [Switch]
     $StayConnected = $false
   )

   $graphAppId = "00000003-0000-0000-c000-000000000000"

   # Requires an admin
   Connect-MgGraph -Scopes "Application.ReadWrite.All AppRoleAssignment.ReadWrite.All User.Read" -UseDeviceAuthentication -ErrorAction Stop

   # Get context for access to tenant ID
   $context = Get-MgContext -ErrorAction Stop
   $authTenant = $context.TenantId

   # Create app registration
   $appRegistration = New-MgApplication -DisplayName $AppName -SignInAudience "AzureADMyOrg" -ErrorAction Stop
   Write-Host -ForegroundColor Cyan "App registration created with app ID" $appRegistration.AppId

   # Create corresponding service principal
   $appServicePrincipal = New-MgServicePrincipal -AppId $appRegistration.AppId -ErrorAction SilentlyContinue `
     -ErrorVariable SPError
   if ($SPError)
   {
     Write-Host -ForegroundColor Red "A service principal for the app could not be created."
     Write-Host -ForegroundColor Red $SPError
     Exit
   }

   Write-Host -ForegroundColor Cyan "Service principal created"

   # Lookup available Graph application permissions
   $graphServicePrincipal = Get-MgServicePrincipal -Filter ("appId eq '" + $graphAppId + "'") -ErrorAction Stop
   $graphAppPermissions = $graphServicePrincipal.AppRoles

   $resourceAccess = @()

   foreach($scope in $GraphScopes)
   {
     $permission = $graphAppPermissions | Where-Object { $_.Value -eq $scope }
     if ($permission)
     {
       $resourceAccess += @{ Id =  $permission.Id; Type = "Role"}
     }
     else
     {
       Write-Host -ForegroundColor Red "Invalid scope:" $scope
       Exit
     }
   }

   # Add the permissions to required resource access
   Update-MgApplication -ApplicationId $appRegistration.Id -RequiredResourceAccess `
    @{ ResourceAppId = $graphAppId; ResourceAccess = $resourceAccess } -ErrorAction Stop
   Write-Host -ForegroundColor Cyan "Added application permissions to app registration"

   # Add admin consent
   foreach ($appRole in $resourceAccess)
   {
     New-MgServicePrincipalAppRoleAssignment -ServicePrincipalId $appServicePrincipal.Id `
      -PrincipalId $appServicePrincipal.Id -ResourceId $graphServicePrincipal.Id `
      -AppRoleId $appRole.Id -ErrorAction SilentlyContinue -ErrorVariable SPError | Out-Null
     if ($SPError)
     {
       Write-Host -ForegroundColor Red "Admin consent for one of the requested scopes could not be added."
       Write-Host -ForegroundColor Red $SPError
       Exit
     }
   }
   Write-Host -ForegroundColor Cyan "Added admin consent"

   # Add a client secret
   $clientSecret = Add-MgApplicationPassword -ApplicationId $appRegistration.Id -PasswordCredential `
    @{ DisplayName = "Added by PowerShell" } -ErrorAction Stop

   Write-Host
   Write-Host -ForegroundColor Green "SUCCESS"
   Write-Host -ForegroundColor Cyan -NoNewline "Client ID: "
   Write-Host -ForegroundColor Yellow $appRegistration.AppId
   Write-Host -ForegroundColor Cyan -NoNewline "Tenant ID: "
   Write-Host -ForegroundColor Yellow $authTenant
   Write-Host -ForegroundColor Cyan -NoNewline "Client secret: "
   Write-Host -ForegroundColor Yellow $clientSecret.SecretText
   Write-Host -ForegroundColor Cyan -NoNewline "Secret expires: "
   Write-Host -ForegroundColor Yellow $clientSecret.EndDateTime

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
3. Open PowerShell and change the current directory to the location of **RegisterAppForAppOnlyAuth.ps1**.
4. Run the following command.

   ```powershell
   .\RegisterAppForAppOnlyAuth.ps1 -AppName "Graph App-Only Auth Tutorial" -GraphScopes "User.Read.All"
   ```

5. Follow the prompt to open `https://microsoft.com/devicelogin` in a browser, enter the provided code, and complete the authentication process.
6. Copy the **Client ID**, **Tenant ID**, and **Client secret** values from the script output. You'll need these values in the next step.

   ```powershell
   SUCCESS
   Client ID: ae2386e6-799e-4f75-b191-855d7e691c75
   Tenant ID: 5927c10a-91bd-4408-9c70-c50bce922b71
   Client secret: ...
   Secret expires: 10/28/2024 5:01:45 PM
   ```

Note

Notice that, unlike the steps when registering for user authentication, in this section you did configure Microsoft Graph permissions on the app registration. App-only auth uses the [client credentials flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow), which requires that permissions be configured on the app registration. See [The .default scope](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent#the-default-scope) for details.

## Create a .NET console app

Begin by creating a new .NET console project using the [.NET CLI](https://learn.microsoft.com/en-us/dotnet/core/tools/).

1. Open your command-line interface \(CLI\) in a directory where you want to create the project. Run the following command.

   ```dotnetcli
   dotnet new console -o GraphAppOnlyTutorial
   ```

2. Once the project is created, verify that it works by changing the current directory to the **GraphAppOnlyTutorial** directory and running the following command in your CLI.

   ```dotnetcli
   dotnet run
   ```


   If it works, the app should output `Hello, World!`.

## Install dependencies

Before moving on, add some dependencies that you use later.

- [.NET configuration packages](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration) to read application configuration from **appsettings.json**.
- [Azure Identity client library for .NET](https://www.nuget.org/packages/Azure.Identity) to authenticate the user and acquire access tokens.
- [Microsoft Graph .NET client library](https://github.com/microsoftgraph/msgraph-sdk-dotnet) to make calls to the Microsoft Graph.

To install the dependencies, run the following commands in your CLI.

```Shell
dotnet add package Microsoft.Extensions.Configuration.Binder
dotnet add package Microsoft.Extensions.Configuration.Json
dotnet add package Microsoft.Extensions.Configuration.UserSecrets
dotnet add package Azure.Identity
dotnet add package Microsoft.Graph
```

## Load application settings

Add the details of your app registration to the project.

1. Create a file in the **GraphAppOnlyTutorial** directory named **appsettings.json** and add the following code.

   ```json
   {
     "settings": {
       "clientId": "YOUR_CLIENT_ID_HERE",
       "tenantId": "YOUR_TENANT_ID_HERE"
     }
   }
   ```

2. Update the values according to the following table.
   | Setting | Value |
   | --- | --- |
   | `clientId` | The client ID of your app registration |
   | `tenantId` | The tenant ID of your organization. |


   Tip


   Optionally, you can set these values in a separate file named **appsettings.Development.json**.

3. Add your client secret to the [.NET Secret Manager](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets). In your command-line interface, change the directory to the location of **GraphAppOnlyTutorial.csproj** and run the following commands, replacing *<client-secret>* with your client secret.

   ```dotnetcli
   dotnet user-secrets init
   dotnet user-secrets set settings:clientSecret <client-secret>
   ```

4. Update **GraphAppOnlyTutorial.csproj** to copy **appsettings.json** to the output directory. Add the following code between the `<Project>` and `</Project>` lines.

   ```xml
   <ItemGroup>
     <None Include="appsettings*.json">
       <CopyToOutputDirectory>Always</CopyToOutputDirectory>
     </None>
   </ItemGroup>
   ```

5. Create a file in the **GraphAppOnlyTutorial** directory named **Settings.cs** and add the following code.

   ```csharp
   using Microsoft.Extensions.Configuration;

   namespace GraphAppOnlyTutorial;

   public class Settings
   {
       public string? ClientId { get; set; }

       public string? ClientSecret { get; set; }

       public string? TenantId { get; set; }

       public static Settings LoadSettings()
       {
           // Load settings
           IConfiguration config = new ConfigurationBuilder()
               /* appsettings.json is required */
               .AddJsonFile("appsettings.json", optional: false)
               /* appsettings.Development.json" is optional, values override appsettings.json */
               .AddJsonFile($"appsettings.Development.json", optional: true)
               /* User secrets are optional, values override both JSON files */
               .AddUserSecrets<Program>()
               .Build();

           return config.GetRequiredSection("Settings").Get<Settings>() ??
               throw new Exception("Could not load app settings. See README for configuration instructions.");
       }
   }
   ```

## Design the app

Create a console-based menu.

1. Open **./Program.cs** and replace its entire contents with the following code.

   ```csharp
   using GraphAppOnlyTutorial;

   Console.WriteLine(".NET Graph App-only Tutorial\n");

   var settings = Settings.LoadSettings();

   // Initialize Graph
   InitializeGraph(settings);

   int choice = -1;

   while (choice != 0)
   {
       Console.WriteLine("Please choose one of the following options:");
       Console.WriteLine("0. Exit");
       Console.WriteLine("1. Display access token");
       Console.WriteLine("2. List users");
       Console.WriteLine("3. Make a Graph call");

       try
       {
           choice = int.Parse(Console.ReadLine() ?? string.Empty);
       }
       catch (System.FormatException)
       {
           // Set to invalid value
           choice = -1;
       }

       switch (choice)
       {
           case 0:
               // Exit the program
               Console.WriteLine("Goodbye...");
               break;
           case 1:
               // Display access token
               await DisplayAccessTokenAsync();
               break;
           case 2:
               // List users
               await ListUsersAsync();
               break;
           case 3:
               // Run any Graph code
               await MakeGraphCallAsync();
               break;
           default:
               Console.WriteLine("Invalid choice! Please try again.");
               break;
       }
   }
   ```

2. Add the following placeholder methods at the end of the file. You implement them in later steps.

   ```csharp
   void InitializeGraph(Settings settings)
   {
       // TODO
   }

   async Task DisplayAccessTokenAsync()
   {
       // TODO
   }

   async Task ListUsersAsync()
   {
       // TODO
   }

   async Task MakeGraphCallAsync()
   {
       // TODO
   }
   ```

This implements a basic menu and reads the user's choice from the command line.

## Next step

[Add app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only-authentication)
