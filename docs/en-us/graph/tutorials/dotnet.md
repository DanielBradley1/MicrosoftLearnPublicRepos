<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/dotnet -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Build .NET apps with Microsoft Graph

This tutorial teaches you how to build a .NET console app that uses the Microsoft Graph API to access data on behalf of a user.

Note

To learn how to use Microsoft Graph to access data using app-only authentication, see this [app-only authentication tutorial](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only).

In this tutorial, you will:

- [Get the signed-in user](https://learn.microsoft.com/en-us/graph/api/user-get)
- [List the user's inbox messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages)
- [Send an email](https://learn.microsoft.com/en-us/graph/api/user-sendmail)

Tip

As an alternative to following this tutorial, you can download the completed code through the [quick start](https://developer.microsoft.com/graph/quick-start?state=option-dotnet) tool, which automates app registration and configuration. The downloaded code works without any modifications required.

You can also download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-dotnet) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have the [.NET SDK](https://dotnet.microsoft.com/download) installed on your development machine.

You should also have a Microsoft work or school account with an Exchange Online mailbox. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a one-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/microsoft-365/try).

Note

This tutorial was written with .NET SDK version 7.0.102. The steps in this guide might work with other versions, but that hasn't been tested.

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

## Create a .NET console app

Begin by creating a new .NET console project using the [.NET CLI](https://learn.microsoft.com/en-us/dotnet/core/tools/).

1. Open your command-line interface \(CLI\) in a directory where you want to create the project. Run the following command.

   ```dotnetcli
   dotnet new console -o GraphTutorial
   ```

2. Once the project is created, verify that it works by changing the current directory to the **GraphTutorial** directory and running the following command in your CLI.

   ```dotnetcli
   dotnet run
   ```


   If it works, the app should output `Hello, World!`.

## Install dependencies

Before moving on, add dependencies that you use later.

- [.NET configuration packages](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration) to read application configuration from **appsettings.json**.
- [Azure Identity client library for .NET](https://www.nuget.org/packages/Azure.Identity) to authenticate the user and acquire access tokens.
- [Microsoft Graph .NET client library](https://github.com/microsoftgraph/msgraph-sdk-dotnet) to make calls to the Microsoft Graph.

To install dependencies, run the following commands in your CLI.

```Shell
dotnet add package Microsoft.Extensions.Configuration.Binder
dotnet add package Microsoft.Extensions.Configuration.Json
dotnet add package Microsoft.Extensions.Configuration.UserSecrets
dotnet add package Azure.Identity
dotnet add package Microsoft.Graph
```

## Load application settings

Next, add the details of your app registration to the project.

1. Create a file in the **GraphTutorial** directory named **appsettings.json** and add the following code.

   ```json
   {
     "settings": {
       "clientId": "YOUR_CLIENT_ID_HERE",
       "tenantId": "common",
       "graphUserScopes": [
         "user.read",
         "mail.read",
         "mail.send"
       ]
     }
   }
   ```

2. Update the values according to the following table.
   | Setting | Value |
   | --- | --- |
   | `clientId` | The client ID of your app registration |
   | `tenantId` | If you chose the option to only allow users in your organization to sign in, change this value to your tenant ID. Otherwise leave as `common`. |


   Tip


   Optionally, you can set these values in a separate file named **appsettings.Development.json**, or in the [.NET Secret Manager](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets).

3. Update **GraphTutorial.csproj** to copy **appsettings.json** to the output directory. Add the following code between the `<Project>` and `</Project>` lines.

   ```xml
   <ItemGroup>
     <None Include="appsettings*.json">
       <CopyToOutputDirectory>Always</CopyToOutputDirectory>
     </None>
   </ItemGroup>
   ```

4. Create a file in the **GraphTutorial** directory named **Settings.cs** and add the following code.

   ```csharp
   using Microsoft.Extensions.Configuration;

   namespace GraphTutorial;

   public class Settings
   {
       public string? ClientId { get; set; }

       public string? TenantId { get; set; }

       public string[]? GraphUserScopes { get; set; }

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

Continue by creating a simple console-based menu.

1. Open **./Program.cs** and replace its entire contents with the following code.

   ```csharp
   using GraphTutorial;

   Console.WriteLine(".NET Graph Tutorial\n");

   var settings = Settings.LoadSettings();

   // Initialize Graph
   InitializeGraph(settings);

   // Greet the user by name
   await GreetUserAsync();

   int choice = -1;

   while (choice != 0)
   {
       Console.WriteLine("Please choose one of the following options:");
       Console.WriteLine("0. Exit");
       Console.WriteLine("1. Display access token");
       Console.WriteLine("2. List my inbox");
       Console.WriteLine("3. Send mail");
       Console.WriteLine("4. Make a Graph call");

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
               // List emails from user's inbox
               await ListInboxAsync();
               break;
           case 3:
               // Send an email message
               await SendMailAsync();
               break;
           case 4:
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

   async Task GreetUserAsync()
   {
       // TODO
   }

   async Task DisplayAccessTokenAsync()
   {
       // TODO
   }

   async Task ListInboxAsync()
   {
       // TODO
   }

   async Task SendMailAsync()
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

[Add user authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-authentication)
