<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/ -->
<!-- Sitemap-Last-Modified: 2024-03-26 -->

# Microsoft Authentication Library for Android

The Microsoft Authentication Library \(MSAL\) for Android is a library that enables Android applications to authenticate users with Microsoft identity platform \(formerly Azure Active Directory\) and access protected web APIs using OAuth2 and OpenID Connect protocols. MSAL Android enables developers to acquire security tokens from the Microsoft identity platform to authenticate users and access secure web APIs for their Android based applications.

MSAL Android supports multiple authentication scenarios, such as single sign-on \(SSO\), conditional access, and brokered authentication. It allows you to easily target several identities including Microsoft Entra ID \(Work and School accounts\), Microsoft Accounts \(Outlook.com, hotmail.com, and several others\), or Azure AD B2C \(Social and Local accounts\).

The guidance here is intended to document common functionalities related to MSAL Android. If you're looking for more help getting started with Microsoft Entra ID, Microsoft Accounts, or Azure AD B2C, check out the [Microsoft identity platform docs](https://aka.ms/aaddev). If you're looking for more info about the Microsoft Graph API, check out the [Microsoft Graph docs](https://graph.microsoft.io).

## Native authentication support in MSAL

MSAL Android also enables you to implement a native authentication experience with end-to-end customizable flows in mobile applications. With native authentication, users are guided through a rich, native, mobile-first sign-up and sign-in journey without leaving the app. The native authentication feature is only available for mobile apps on [External ID for customers](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-native-authentication).

## Migrating from Azure Active Directory Authentication Library \(ADAL\)

The Azure Active Directory Authentication Library \(ADAL\) for Android has been deprecated effective June 2023. If you or your organization are using the Azure Active Directory Authentication Library \(ADAL\) for Android, you should [migrate to MSAL Android](https://learn.microsoft.com/en-us/entra/msal/android/migrate-android-adal-msal) to avoid putting your app's security at risk. Microsoft Authentication Library \(MSAL\) for Android is the supported library that can be used for authentication and token acquisition.

## Getting started with MSAL Android

To use MSAL Android in your application, you need to:

- [Register your app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) with Microsoft Entra ID.
- Learn about the [types of client applications](https://learn.microsoft.com/en-us/entra/identity-platform/msal-client-applications): public clients and confidential clients.

Since MSAL Android supports both browser-delegated and native authentication experiences, follow the steps in the following tutorials based on your scenario.

- For browser-delegated authentication scenarios, refer to the quickstart, [Sign in users and call Microsoft Graph from an Android app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-android-sign-in).
- For native authentication scenarios, refer to the Microsoft Entra External ID sample guide, [Tutorial: Prepare your Android app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-android-app).

### Requirements

- Min SDK Version 16+
- Target SDK Version 33+

### Step 1: Declare dependency on MSAL

Add to your app's build.gradle:

```gradle
dependencies {
    implementation 'com.microsoft.identity.client:msal:4.9.+'
}
```

Please also add the following lines to your repositories section in your gradle script:

```gradle
maven { 
    url 'https://pkgs.dev.azure.com/MicrosoftDeviceSDK/DuoSDK-Public/_packaging/Duo-SDK-Feed/maven/v1' 
}
```

### Step 2: Create your MSAL configuration file

**Browser-delegated authentication:**

Create your configuration file as a "raw" resource in your project. Refer to it using the generated resource identifier when constructing a `PublicClientApplication` instance.. If you're registering your app in the Microsoft Entra admin center for the first time, you'll also be provided with the detailed MSAL [Android configuration file](https://learn.microsoft.com/en-us/entra/msal/android/msal-configuration)

```javascript
{
  "client_id" : "<YOUR_CLIENT_ID>",
  "redirect_uri" : "msauth://<YOUR_PACKAGE_NAME>/<YOUR_BASE64_URL_ENCODED_PACKAGE_SIGNATURE>",
  "broker_redirect_uri_registered": true,
}
```

In the `redirect_uri`, the `<YOUR_PACKAGE_NAME>` refers to the package name returned by the `context.getPackageName()` method. This package name is the same as the [`application_id`](https://developer.android.com/studio/build/application-id) defined in your `build.gradle` file.

The values above are the minimum required configuration. MSAL relies on the defaults that ship with the library for all other settings. Please refer to the [MSAL Android configuration file documentation](https://learn.microsoft.com/en-us/entra/msal/android/msal-configuration) to understand the library defaults.

**Native authentication:**

1. Right-click res and choose New > Directory. Enter raw as the new directory name and select OK.
2. In this new folder \(app > src > main > res > raw\), create a new JSON file called auth\_config\_native\_auth.json and paste the following template MSAL Configuration:

```
{ 
  "client_id": "Enter_the_Application_Id_Here", 
  "authorities": [ 
    { 
      "type": "CIAM", 
      "authority_url": "https://Enter_the_Tenant_Subdomain_Here.ciamlogin.com/Enter_the_Tenant_Subdomain_Here.onmicrosoft.com/" 
    } 
  ], 
  "challenge_types": ["oob"], 
  "logging": { 
    "pii_enabled": false, 
    "log_level": "INFO", 
    "logcat_enabled": true 
  } 
 }
```

### Step 3: Configure the AndroidManifest.xml for browser-delegated authentication

1. Request the following permissions via the Android Manifest

```XML
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```

2. Configure an intent filter in the Android Manifest, using your redirect URI

Failure to include an intent filter matching the redirect URI you specify via configuration will result in a failed interactive token request.

```XML
    <!--Intent filter to capture authorization code response from the default browser on the device calling back to our app after interactive sign in -->
    <activity
        android:name="com.microsoft.identity.client.BrowserTabActivity">
        <intent-filter>
            <action android:name="android.intent.action.VIEW" />
            <category android:name="android.intent.category.DEFAULT" />
            <category android:name="android.intent.category.BROWSABLE" />
            <data
                android:scheme="msauth"
                android:host="<YOUR_PACKAGE_NAME>"
                android:path="/<YOUR_BASE64_ENCODED_PACKAGE_SIGNATURE>" />
        </intent-filter>
    </activity>
```

You can refer to the [MSAL Android FAQ](https://learn.microsoft.com/en-us/entra/msal/android/frequently-asked-questions) for more information on common redirect uri issues.

## ProGuard

MSAL uses reflection and generic type information stored in `.class` files at runtime to support various persistence and serialization related functionalities. Library support for minification and obfuscation is limited. A default configuration is shipped with this library; please [file an issue](https://github.com/AzureAD/microsoft-authentication-library-for-android/issues/new/choose) if you find any issues.

## Recommendation

MSAL is a security library. It controls how users sign-in and access services. We recommend you always take the latest version of our library in your app when you can. We use [semantic versioning](http://semver.org) so you can control the risk of updating your app. For example, always downloading the latest minor version number \(e.g. x.*y*.x\) ensures you get the latest security and feature enhanements with the assurance that our API surface area has not changed. You can always see the latest version and release notes under the [Releases](https://github.com/AzureAD/microsoft-authentication-library-for-android/releases) tab of GitHub.
