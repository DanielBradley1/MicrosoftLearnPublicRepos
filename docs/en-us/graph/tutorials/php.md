<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/php -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Build PHP apps with Microsoft Graph

This tutorial teaches you how to build a PHP console app that uses the Microsoft Graph API to access data on behalf of a user.

Note

To learn how to use Microsoft Graph to access data using app-only authentication, see this [app-only authentication tutorial](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only).

In this tutorial, you will:

- [Get the signed-in user](https://learn.microsoft.com/en-us/graph/api/user-get)
- [List the user's inbox messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages)
- [Send an email](https://learn.microsoft.com/en-us/graph/api/user-sendmail)

Tip

As an alternative to following this tutorial, you can download the completed code through the [quick start](https://developer.microsoft.com/graph/quick-start?state=option-php) tool, which automates app registration and configuration. The downloaded code works without any modifications required.

You can also download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-php) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have [PHP](https://www.php.net/) and [Composer](https://getcomposer.org/) installed on your development machine.

You should also have a Microsoft work or school account with an Exchange Online mailbox. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a one-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/microsoft-365/try).

Note

This tutorial was written with PHP version 8.1.5 and Composer version 2.3.5. The steps in this guide might work with other versions, but that hasn't been tested.

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

## Create a PHP console app

Begin by initializing a new Composer project. Open your command-line interface \(CLI\) in a directory where you want to create the project. Run the following command.

```bash
composer init
```

Answer the prompts. You can accept the defaults for most questions, but respond `n` to the following questions:

```bash
Would you like to define your dependencies (require) interactively [yes]? n
Would you like to define your dev dependencies (require-dev) interactively [yes]? n
Add PSR-4 autoload mapping? Maps namespace "Microsoft\Graphtutorial" to the entered relative path. [src/, n to skip]: n
```

## Install dependencies

Before moving on, add dependencies that you use later.

- [Microsoft Graph SDK for PHP](https://github.com/microsoftgraph/msgraph-sdk-php) to make calls to the Microsoft Graph.
- [vlucas/phpdotenv](https://github.com/vlucas/phpdotenv) for reading environment variables from .env files.

To install the dependencies, run the following command in your CLI.

```bash
composer require microsoft/microsoft-graph vlucas/phpdotenv
```

## Load application settings

Next, add the details of your app registration to the project.

1. Create a file in the root directory of your project named **.env** and add the following code.

   ```ini
   CLIENT_ID=YOUR_CLIENT_ID_HERE
   TENANT_ID=common
   GRAPH_USER_SCOPES='user.read mail.read mail.send'
   ```

2. Update the values according to the following table.
   | Setting | Value |
   | --- | --- |
   | `CLIENT_ID` | The client ID of your app registration |
   | `TENANT_ID` | If you chose the option to only allow users in your organization to sign in, change this value to your tenant ID. Otherwise leave as `common`. |


   Important


   If you're using source control such as git, now would be a good time to exclude the **.env** file from source control to avoid inadvertently leaking your app ID.

## Design the app

Continue by creating a simple console-based menu.

1. Create a file in the root directory of your project named **main.php**. Add the opening and closing PHP tags.

   ```php
   <?php
   ?>
   ```

2. Add the following code between the PHP tags.

   ```php
   // Enable loading of Composer dependencies
   require_once realpath(__DIR__ . '/vendor/autoload.php');
   require_once 'GraphHelper.php';

   print('PHP Graph Tutorial'.PHP_EOL.PHP_EOL);

   // Load .env file
   $dotenv = Dotenv\Dotenv::createImmutable(__DIR__);
   $dotenv->load();
   $dotenv->required(['CLIENT_ID', 'TENANT_ID', 'GRAPH_USER_SCOPES']);

   initializeGraph();

   greetUser();

   $choice = -1;

   while ($choice != 0) {
       echo('Please choose one of the following options:'.PHP_EOL);
       echo('0. Exit'.PHP_EOL);
       echo('1. Display access token'.PHP_EOL);
       echo('2. List my inbox'.PHP_EOL);
       echo('3. Send mail'.PHP_EOL);
       echo('4. Make a Graph call'.PHP_EOL);

       $choice = (int)readline('');

       switch ($choice) {
           case 1:
               displayAccessToken();
               break;
           case 2:
               listInbox();
               break;
           case 3:
               sendMail();
               break;
           case 4:
               makeGraphCall();
               break;
           case 0:
           default:
               print('Goodbye...'.PHP_EOL);
       }
   }
   ```

3. Add the following placeholder methods at the end of the file before the closing PHP tag. You implement them in later steps.

   ```php
   function initializeGraph(): void {
       // TODO
   }

   function greetUser(): void {
       // TODO
   }

   function displayAccessToken(): void {
       // TODO
   }

   function listInbox(): void {
       // TODO
   }

   function sendMail(): void {
       // TODO
   }

   function makeGraphCall(): void {
       // TODO
   }
   ```

This implements a basic menu and reads the user's choice from the command line.

## Next step

[Add user authentication](https://learn.microsoft.com/en-us/graph/tutorials/php-authentication)
