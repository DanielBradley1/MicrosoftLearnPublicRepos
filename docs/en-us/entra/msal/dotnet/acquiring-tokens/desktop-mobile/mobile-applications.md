<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/acquiring-tokens/desktop-mobile/mobile-applications -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Using MSAL.NET With MAUI

MSAL.NET can run on mobile devices \(both iOS and Android\) through applications built with [.NET Multi-platform App UI \(MAUI\)](https://dotnet.microsoft.com/apps/maui).

Note

The .NET team recommends [migrating existing Xamarin applications to MAUI](https://learn.microsoft.com/en-us/dotnet/maui/migration/). New applications should always use MAUI. MSAL.NET versions 4.61.0 and above do not provide support for Xamarin Android and Xamarin iOS.

## Using MSAL.NET with brokers on mobile devices

MSAL.NET can be used with authentication brokers on mobile devices, such as Microsoft Authenticator or the Company Portal. To learn more about how to configure applications to use brokers on iOS and Android, refer to [Use Microsoft Authenticator or Intune Company Portal on Xamarin applications](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-use-brokers-with-xamarin-apps).

## MAUI on Android

To get started with MSAL.NET integration on Android, refer to the following resources:

- [How to migrate Xamarin ADAL apps to MSAL for Android](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-migration-android-broker)
- [Xamarin Android Configuration Tips + Troubleshooting](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-xamarin-android-considerations)
- [Xamarin Android System Browser Info](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-system-browser-android-considerations)

To learn more about testing MSAL on Android devices, refer to the [MSAL for Android Wiki](https://github.com/AzureAD/microsoft-authentication-library-for-android/wiki/Android-Emulator-with-MSAL).

## MAUI on iOS

To get started with MSAL.NET integration on iOS, refer to the following resources:

- [How to migrate Xamarin ADAL apps to MSAL for iOS](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-migration-ios-broker)
- [Xamarin iOS Configuration Tips + Troubleshooting](https://learn.microsoft.com/en-us/entra/identity-platform/msal-net-xamarin-ios-considerations)
