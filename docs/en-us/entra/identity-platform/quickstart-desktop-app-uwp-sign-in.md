<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-desktop-app-uwp-sign-in -->
<!-- Sitemap-Last-Modified: 2024-05-19 -->

# Quickstart: Sign in users and call Microsoft Graph in a Universal Windows Platform app

In this quickstart, you download and run a code sample that demonstrates how a Universal Windows Platform \(UWP\) application can sign in users and get an access token to call the Microsoft Graph API.

See [How the sample works](#how-the-sample-works) for an illustration.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- [Visual Studio](https://visualstudio.microsoft.com/vs/)

Note

MSAL.NET versions 4.61.0 and above do not provide support for Universal Windows Platform \(UWP\), Xamarin Android, and Xamarin iOS. We recommend you migrate your UWP applications to modern frameworks like WINUI. Read more about the deprecation in [Announcing the Upcoming Deprecation of MSAL.NET for Xamarin and UWP](https://devblogs.microsoft.com/identity/uwp-xamarin-msal-net-deprecation/).

## Register and download your quickstart app

You have two options to start your quickstart application:

- \[Express\] [Option 1: Register and auto configure your app and then download your code sample](#option-1-register-and-auto-configure-your-app-and-then-download-your-code-sample)
- \[Manual\] [Option 2: Register and manually configure your application and code sample](#option-2-register-and-manually-configure-your-application-and-code-sample)

### Option 1: Register and auto configure your app and then download your code sample

1. Go to the [AMicrosoft Entra admin center - App registrations](https://entra.microsoft.com/#blade/Microsoft_AAD_RegisteredApps/applicationsListBlade/quickStartType/UwpQuickstartPage/sourceType/docs) quickstart experience.
2. Enter a name for your application and select **Register**.
3. Follow the instructions to download and automatically configure your new application.

### Option 2: Register and manually configure your application and code sample

#### Step 1: Register your application

To register your application and add the app's registration information to your solution, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/admin-center-settings-icon.png) in the top menu to switch to the tenant in which you want to register the application from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **App registrations**, select **New registration**.
4. Enter a **Name** for your application, for example `UWP-App-calling-MsGraph`. Users of your app might see this name, and you can change it later.
5. In the **Supported account types** section, select **Accounts in any organizational directory and personal Microsoft accounts \(for example, Skype, Xbox, Outlook.com\)**.
6. Select **Register** to create the application, and then record the **Application \(client\) ID** for use in a later step.
7. Under **Manage**, select **Authentication**.
8. Select **Add a platform** > **Mobile and desktop applications**.
9. Under **Redirect URIs**, select `https://login.microsoftonline.com/common/oauth2/nativeclient`.
10. Select **Configure**.

#### Step 2: Download the project

[Download the UWP sample application](https://github.com/Azure-Samples/active-directory-dotnet-native-uwp-v2/archive/msal3x.zip)

Tip

To avoid errors caused by path length limitations in Windows, we recommend extracting the archive or cloning the repository into a directory near the root of your drive.

#### Step 3: Configure the project

1. Extract the .zip archive to a local folder close to the root of your drive. For example, into **C:\\Azure-Samples**.
2. Open the project in Visual Studio. Install the **Universal Windows Platform development** workload and any individual SDK components if prompted.
3. In *MainPage.Xaml.cs*, change the value of the `ClientId` variable to the **Application \(Client\) ID** of the application you registered earlier.

   ```csharp
   private const string ClientId = "Enter_the_Application_Id_here";
   ```


   You can find the **Application \(client\) ID** on the app's **Overview** pane in the Microsoft Entra admin center \(**Entra ID** > **App registrations** > *{Your app registration}*\).

4. Create and then select a new self-signed test certificate for the package:

   1. In the **Solution Explorer**, double-click the *Package.appxmanifest* file.
   2. Select **Packaging** > **Choose Certificate...** > **Create...**.
   3. Enter a password and then select **OK**. A certificate called *Native\_UWP\_V2\_TemporaryKey.pfx* is created.
   4. Select **OK** to dismiss the **Choose a certificate** dialog, and then verify that you see *Native\_UWP\_V2\_TemporaryKey.pfx* in Solution Explorer.
   5. In the **Solution Explorer**, right-click the **Native\_UWP\_V2** project and select **Properties**.
   6. Select **Signing**, and then select the .pfx you created in the **Choose a strong name key file** drop-down.

#### Step 4: Run the application

To run the sample application on your local machine:

1. In the Visual Studio toolbar, choose the right platform \(probably **x64** or **x86**, not ARM\). The target device should change from *Device* to *Local Machine*.
2. Select **Debug** > **Start Without Debugging**.

   If you're prompted to do so, you might first need to enable **Developer Mode**, and then **Start Without Debugging** again to launch the app.

When the app's window appears, you can select the **Call Microsoft Graph API** button, enter your credentials, and consent to the permissions requested by the application. If successful, the application displays some token information and data obtained from the call to the Microsoft Graph API.

## How the sample works

![Diagram showing how the sample app generated by this quickstart works.](https://learn.microsoft.com/en-us/entra/identity-platform/media/quickstart-v2-uwp/uwp-intro.svg)

### MSAL.NET

MSAL \([Microsoft.Identity.Client](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client)\) is the library used to sign in users and request security tokens. The security tokens are used to access an API protected by the Microsoft identity platform. You can install MSAL by running the following command in Visual Studio's *Package Manager Console*:

```powershell
Install-Package Microsoft.Identity.Client
```

### MSAL initialization

You can add the reference for MSAL by adding the following code:

```csharp
using Microsoft.Identity.Client;
```

Then, MSAL is initialized using the following code:

```csharp
public static IPublicClientApplication PublicClientApp;
PublicClientApp = PublicClientApplicationBuilder.Create(ClientId)
                                                .WithRedirectUri("https://login.microsoftonline.com/common/oauth2/nativeclient")
                                                    .Build();
```

The value of `ClientId` is the **Application \(client\) ID** of the app you registered in the Microsoft Entra admin center. You can find this value in the app's **Overview** page in the Microsoft Entra admin center.

### Requesting tokens

MSAL has two methods for acquiring tokens in a UWP app: [`AcquireTokenInteractive`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.acquiretokeninteractiveparameterbuilder) and [`AcquireTokenSilent`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.acquiretokensilentparameterbuilder).

#### Get a user token interactively

Some situations require forcing users to interact with the Microsoft identity platform through a pop-up window to either validate their credentials or to give consent. Some examples include:

- The first-time users sign in to the application
- When users may need to reenter their credentials because the password has expired
- When your application is requesting access to a resource, that the user needs to consent to
- When two factor authentication is required

```csharp
authResult = await PublicClientApp.AcquireTokenInteractive(scopes)
                      .ExecuteAsync();
```

The `scopes` parameter contains the scopes being requested, such as `{ "user.read" }` for Microsoft Graph or `{ "api://<Application ID>/access_as_user" }` for custom web APIs.

#### Get a user token silently

Use the `AcquireTokenSilent` method to obtain tokens to access protected resources after the initial `AcquireTokenInteractive` method. You don’t want to require the user to validate their credentials every time they need to access a resource. Most of the time you want token acquisitions and renewal without any user interaction

```csharp
var accounts = await PublicClientApp.GetAccountsAsync();
var firstAccount = accounts.FirstOrDefault();
authResult = await PublicClientApp.AcquireTokenSilent(scopes, firstAccount)
                                      .ExecuteAsync();
```

- `scopes` contains the scopes being requested, such as `{ "user.read" }` for Microsoft Graph or `{ "api://<Application ID>/access_as_user" }` for custom web APIs.
- `firstAccount` specifies the first user account in the cache \(MSAL supports multiple users in a single app\).

## Help and support

If you need help, want to report an issue, or want to learn about your support options, see [Help and support for developers](https://learn.microsoft.com/en-us/entra/identity-platform/developer-support-help-options).

## Next steps

Try out the Windows desktop tutorial for a complete step-by-step guide on building applications and new features, including a full explanation of this quickstart.

[UWP - Call Graph API tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-windows-uwp)
