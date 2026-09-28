<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/migrate-android-broker -->
<!-- Sitemap-Last-Modified: 2023-09-05 -->

# Migrate Android applications that use a broker from ADAL.NET to MSAL.NET

If you have a Xamarin Android app currently using the Azure Active Directory Authentication Library for .NET \(ADAL.NET\) and an [authentication broker](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-android-single-sign-on), it's time to migrate to the [Microsoft Authentication Library for .NET](https://learn.microsoft.com/en-us/entra/msal) \(MSAL.NET\).

## Prerequisites

- A Xamarin Android app already integrated with a broker \([Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) or [Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)\) and ADAL.NET that you need to migrate to MSAL.NET.

## Step 1: Enable the broker

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| In ADAL.NET, broker support is enabled on a per-authentication context basis.<br><br>To call the broker, you had to set a `useBroker` to *true* in the `PlatformParameters` constructor:<br><br>```CSharp<br>public PlatformParameters(<br>        Activity callerActivity,<br>        bool useBroker)<br>```<br><br>In the platform-specific page renderer code for Android, you set the `useBroker` flag to true:<br><br>```CSharp<br>page.BrokerParameters = new PlatformParameters(<br>        this,<br>        true,<br>        PromptBehavior.SelectAccount);<br>```<br><br>Then, include the parameters in the acquire token call:<br><br>```CSharp<br>AuthenticationResult result =<br>        await<br>            AuthContext.AcquireTokenAsync(<br>                Resource,<br>                ClientId,<br>                new Uri(RedirectURI),<br>                platformParameters)<br>                .ConfigureAwait(false);<br>``` | In MSAL.NET, broker support is enabled on a per-PublicClientApplication basis.<br><br>Use the `WithBroker()` parameter \(which is set to true by default\) to call broker:<br><br>```CSharp<br>var app = PublicClientApplicationBuilder<br>                .Create(ClientId)<br>                .WithBroker()<br>                .WithRedirectUri(redirectUriOnAndroid)<br>                .Build();<br>```<br><br>Then, in the AcquireToken call:<br><br>```CSharp<br>result = await app.AcquireTokenInteractive(scopes)<br>             .WithParentActivityOrWindow(App.RootViewController)<br>             .ExecuteAsync();<br>``` |

## Step 2: Set an Activity

In ADAL.NET, you passed in an activity \(usually the MainActivity\) as part of the PlatformParameters as shown in [Step 1: Enable the broker](#step-1-enable-the-broker).

MSAL.NET also uses an activity, but it's not required in regular Android usage without a broker. To use the broker, set the activity to send and receive responses from broker.

| Current ADAL code: | MSAL counterpart: |
| --- | --- |
| The activity is passed into the PlatformParameters in the Android-specific platform.<br><br>```CSharp<br>page.BrokerParameters = new PlatformParameters(<br>          this,<br>          true,<br>          PromptBehavior.SelectAccount);<br>``` | In MSAL.NET, do two things to set the activity for Android:<br><br>1. In `MainActivity.cs`, set the `App.RootViewController` to the `MainActivity` to ensure there's an activity with the call to the broker.<br><br>   If it's not set correctly, you may get this error: `"Activity_required_for_android_broker":"Activity is null, so MSAL.NET cannot invoke the Android broker. See https://aka.ms/Brokered-Authentication-for-Android"`<br>2. On the AcquireTokenInteractive call, use the `.WithParentActivityOrWindow(App.RootViewController)` and pass in the reference to the activity you will use. This example will use the MainActivity.<br><br>**For example:**<br><br>In *App.cs*:<br><br>```CSharp<br>   public static object RootViewController { get; set; }<br>```<br><br>In *MainActivity.cs*:<br><br>```CSharp<br>   LoadApplication(new App());<br>   App.RootViewController = this;<br>```<br><br>In the AcquireToken call:<br><br>```CSharp<br>result = await app.AcquireTokenInteractive(scopes)<br>             .WithParentActivityOrWindow(App.RootViewController)<br>             .ExecuteAsync();<br>``` |

## Next steps

For more information about Android-specific considerations when using MSAL.NET with Xamarin, see [Configuration requirements and troubleshooting tips for Xamarin Android with MSAL.NET](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-xamarin-android-considerations).
