<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-ios-broker -->
<!-- Sitemap-Last-Modified: 2024-11-01 -->

# Migrate iOS applications that use Microsoft Authenticator from ADAL.NET to MSAL.NET

Warning

Azure Active Directory Authentication Library \(ADAL\) **has been deprecated**. While existing apps that use ADAL will continue to work, Microsoft will no longer release security fixes on ADAL. Use the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/msal/) to avoid putting your app's security at risk.

If you've been using the Azure Active Directory Authentication Library for .NET \(ADAL.NET\) and the iOS broker, you need to migrate to the Microsoft Authentication Library \(MSAL\) for .NET, which supports the broker on iOS starting with version 4.3. This article helps you migrate your .NET iOS application from ADAL to MSAL.

## Prerequisites

This article assumes that you have a MAUI or Xamarin iOS app that's integrated with the iOS broker. If you do not have an existing ADAL-based application you can use MSAL.NET directly use the built-in broker implementation in the library. For information on how to invoke the iOS broker in MSAL.NET with a new application, see [Using MSAL.NET With MAUI](https://learn.microsoft.com/en-us/entra/msal/dotnet/acquiring-tokens/desktop-mobile/mobile-applications).

## Background

### What are authentication brokers?

Authentication brokers are applications provided by Microsoft on Android and iOS, such as [Microsoft Authenticator](https://support.microsoft.com/en-us/account-billing/download-microsoft-authenticator-351498fc-850a-45da-b7b6-27e523b8702a) on iOS and Android and the Intune Company Portal app on Android.

Authentication brokers enable the following scenarios:

- Single sign-on \(SSO\).
- Device identification, which is required by some [Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview). For more information, see [Device management](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-conditions#device-platforms).
- Application identification verification, which is also required in some enterprise scenarios. For more information, see [Intune mobile application management \(MAM\)](https://learn.microsoft.com/en-us/mem/intune/apps/app-management).

## Migrate from ADAL to MSAL

### Step 1: Enable the broker

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| In ADAL.NET, broker support was enabled on a per-authentication context basis. It's disabled by default. You had to set a `useBroker` flag to `true` in the `PlatformParameters` constructor to call the broker:<br><br>```csharp<br>public PlatformParameters(<br>        UIViewController callerViewController,<br>        bool useBroker)<br>```<br><br>In the platform-specific code, within the page renderer for iOS, set the `useBroker` flag to true:<br><br>```csharp<br>page.BrokerParameters = new PlatformParameters(<br>          this,<br>          true,<br>          PromptBehavior.SelectAccount);<br>```<br><br>Then, include the parameters in the token acquisition call:<br><br>```csharp<br> AuthenticationResult result =<br>                    await<br>                        AuthContext.AcquireTokenAsync(<br>                              Resource,<br>                              ClientId,<br>                              new Uri(RedirectURI),<br>                              platformParameters)<br>                              .ConfigureAwait(false);<br>``` | In MSAL.NET, broker support is enabled separately for each \[`PublicClientApplication`\]\(xref:Microsoft.Identity.Client.PublicClientApplication\) instance. It's disabled by default. To enable it, use \[`WithBroker\(\)`\]\(xref:Microsoft.Identity.Client.PublicClientApplicationBuilder.WithBroker\(System.Boolean\)\) \(set to true by default\) in order to call the broker:<br><br>```csharp<br>var app = PublicClientApplicationBuilder<br>                .Create(ClientId)<br>                .WithBroker()<br>                .WithReplyUri(redirectUriOnIos)<br>                .Build();<br>```<br><br>In the token acquisition call:<br><br>```csharp<br>result = await app.AcquireTokenInteractive(scopes)<br>             .WithParentActivityOrWindow(App.RootViewController)<br>             .ExecuteAsync();<br>``` |

### Step 2: Set a UIViewController\(\)

In ADAL.NET, you passed in a `UIViewController` as part of `PlatformParameters`. In MSAL.NET, to give developers more flexibility, an object window is used, but it's not required in regular iOS scenarios. To use the broker, set the object window in order to send and receive responses from the broker.

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| A `UIViewController` is passed into `PlatformParameters`.<br><br>```csharp<br>page.BrokerParameters = new PlatformParameters(<br>          this,<br>          true,<br>          PromptBehavior.SelectAccount);<br>``` | In MSAL.NET, you must do two things to set the object window for iOS:<br><br>1. In `AppDelegate.cs`, set `App.RootViewController` to a new `UIViewController()`. This assignment ensures that there's a `UIViewController` with the call to the broker. If it isn't set correctly, you might get this error:<br><br>   `"uiviewcontroller_required_for_ios_broker":"UIViewController is null, so MSAL.NET cannot invoke the iOS broker. See https://aka.ms/msal-net-ios-broker"`<br>2. On the `AcquireTokenInteractive` call, use [`.WithParentActivityOrWindow(App.RootViewController)`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.acquiretokeninteractiveparameterbuilder.withparentactivityorwindow#microsoft-identity-client-acquiretokeninteractiveparameterbuilder-withparentactivityorwindow\(system-object\)) and pass in the reference to the object window you'll use.<br><br>**For example:**<br><br>In `App.cs`:<br><br>```csharp<br>   public static object RootViewController { get; set; }<br>```<br><br>In `AppDelegate.cs`:<br><br>```csharp<br>   LoadApplication(new App());<br>   App.RootViewController = new UIViewController();<br>```<br><br>In the token acquisition call:<br><br>```csharp<br>result = await app.AcquireTokenInteractive(scopes)<br>             .WithParentActivityOrWindow(App.RootViewController)<br>             .ExecuteAsync();<br>``` |

### Step 3: Update AppDelegate to handle the callback

Both ADAL and MSAL call the broker, and the broker in turn calls back to your application through the `OpenUrl` method of the `AppDelegate` class. For more information, see [Update AppDelegate to handle the callback](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-use-brokers-with-xamarin-apps#step-3-update-appdelegate-to-handle-the-callback).

There are no changes here between ADAL.NET and MSAL.NET.

### Step 4: Register a URL scheme

ADAL.NET and MSAL.NET use URLs to invoke the broker and return the broker response back to the app. Register the URL scheme in the `Info.plist` file for your app:

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| The URL scheme is unique to your app. | The `CFBundleURLSchemes` name must include `msauth.` as a prefix, followed by your `CFBundleURLName`.<br><br>For example: `$"msauth.(BundleId")`<br><br>```csharp<br><key>CFBundleURLTypes</key><br><array><br>  <dict><br>    <key>CFBundleTypeRole</key><br>    <string>Editor</string><br>    <key>CFBundleURLName</key><br>    <string>com.yourcompany.xforms</string><br>    <key>CFBundleURLSchemes</key><br>    <array><br>      <string>msauth.com.yourcompany.xforms</string><br>    </array><br>  </dict><br></array><br>```<br><br>Note<br><br>This URL scheme becomes part of the redirect URI that's used to uniquely identify the app when it receives the response from the broker. |

### Step 5: Add the broker identifier to the LSApplicationQueriesSchemes section

ADAL.NET and MSAL.NET both use `-canOpenURL:` to check if the broker is installed on the device. Add the correct identifier for the iOS broker to the `LSApplicationQueriesSchemes` section of the `info.plist` file:

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| Uses `msauth`<br><br>```csharp<br><key>LSApplicationQueriesSchemes</key><br><array><br>     <string>msauth</string><br></array><br>``` | Uses `msauthv2`<br><br>```csharp<br><key>LSApplicationQueriesSchemes</key><br><array><br>     <string>msauthv2</string><br>     <string>msauthv3</string><br></array><br>``` |

### Step 6: Register your redirect URI in the Azure portal

ADAL.NET and MSAL.NET both add an extra requirement on the redirect URI when it targets the broker. Register the redirect URI with your application in the Azure or Microsoft Entra portals.

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| `"<app-scheme>://<your.bundle.id>"`<br><br>Example:<br><br>```http<br>mytestiosapp://com.mycompany.myapp`<br>``` | `$"msauth.{BundleId}://auth"`<br><br>Example:<br><br>```csharp<br>public static string redirectUriOnIos = "msauth.com.yourcompany.XForms://auth";<br>``` |

For more information about how to register the redirect URI in the Azure portal, see [Add a redirect URI to your app registration](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-use-brokers-with-xamarin-apps#step-7-add-a-redirect-uri-to-your-app-registrationn).

### Step 7: Set the Entitlements.plist

Enable keychain access in the `Entitlements.plist` file:

```xml
<key>keychain-access-groups</key>
<array>
  <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
</array>
```

For more information about enabling keychain access, see [Enable keychain access](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-xamarin-ios-considerations#enable-keychain-access).

## Importance of logging with MSAL

Among its many capabilities, Microsoft Authentication Library \(MSAL\) has robust built-in [logging features](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/msal-logging). Enabling logging in your applications ensures that you have a direct line of sight on any authentication issues and can both diagnose them easier for your own application and help the MSAL team quickly address potential problems. We strongly recommend that you enable logging for your applications when deployed in any production scenarios.

## Next steps

Learn about [iOS-specific considerations with MSAL.NET](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-xamarin-ios-considerations).
