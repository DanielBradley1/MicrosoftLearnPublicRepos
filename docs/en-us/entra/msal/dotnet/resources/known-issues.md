<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/resources/known-issues -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Known issues with MSAL.NET

MSAL throws a few types of exceptions, please see [Exceptions](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/).

## Confidential Client

Please read the guide on [High Availability](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/high-availability).

## Public Client

### Device Compliance failures on Windows 10

Users are unable to login interactively and a "Device is not compliant" error is shown when:

- The tenant admin has enabled the "Require device to be marked as compliant" Conditional Access policy
- The app is invoking public client flows \(i.e. rich client apps, not web sites\)
- The app is using the embedded browser control available in ADAL or MSAL \(this is the default for .NET Framework apps\)

#### Mitigation

- The recommended approach is to use [WAM](https://learn.microsoft.com/en-us/entra/msal/dotnet/acquiring-tokens/desktop-mobile/wam).
- You can also configure MSAL to use the system \(default OS\) browser. Details in [Using web browsers \(MSAL.NET\)](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-web-browsers#how-to-use-the-default-os-browser). Both Microsoft Edge and Chrome browsers are able to satisfy the device policy.
- If using ADAL, [**migrate to MSAL**](https://learn.microsoft.com/en-us/entra/identity-platform/msal-migration). There is no mitigation for ADAL.

### Android

On Android, an `AndroidActivityNotFound` exception is thrown when the device does not have a browser with tabs. See [Xamarin Android system browser considerations for using MSAL.NET](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-system-browser-android-considerations#known-issues)

### iOS

Please see [Xamarin iOS Considerations](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-xamarin-ios-considerations#known-issues-with-ios-12-and-authentication).

### Desktop

On a Desktop app, a `StateMismatchError` exception is thrown when the using a long Facebook ID \(via B2C\) in conjunction with the embedded browser. For more details, please [refer to our documentation](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/understanding-statemismatcherror).

## Build issues

Behavior: an error similar to `Microsoft.Windows.SDK.Contracts.targets(4,5): error : Must use PackageReference` is thrown

Starting with version 4.23, MSAL references `Microsoft.Windows.SDK.Contracts`. NuGet can only resolve this reference if the application consuming MSAL references it as `<PackageReference>` and not via the legacy `packages.config` mechanism. See [#2247](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/issues/2247) for details on how to fix this.
