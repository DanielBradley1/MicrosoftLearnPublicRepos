<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/configure-your-app -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# Configure your MSAL Android app

## Introduction

MSAL.Android is highly extensible and allows developers to customize several factors that can change the end user experience, app performance, geographies, and several other fields. To get started configuring your app, you'll want to become familiar with the MSAL configuration object. We'll walk through how this works and how the different knobs your app can turn.

## Basics

### 1. Create your configuration

The configuration object is JSON and lives in a file alongside your app. Feel free to drop it anywhere in your app, but we recommend creating your custom configuration in `res/raw/auth_config.json`.

### 2. Tell MSAL where to look

Next, you need to tell MSAL where to look for your configuration. This is done in the instantiation of `PublicClientApplication`, for example:

```java
sampleApp = new PublicClientApplication(this.getApplicationContext(), R.raw.auth_config);
```

### 3. Define your custom configuration

In the configuration, there are some fields that are required and others that are optional. If you don't specify something that's optional, the library likely has a default or will use the data provided somewhere else to complete your app's configuration profile.

Here's an example configuration with just the essentials that targets all Microsoft Entra ID and Microsoft Account users:

```json
{
  "client_id" : "<CLIENT_ID_FROM_https://apps.dev.microsoft.com>",
  "authorization_user_agent" : "DEFAULT",
  "redirect_uri" : "<CLIENT_ID_FROM_https://apps.dev.microsoft.com>://auth",
  "authorities" : [
    {
      "type": "AAD",
      "audience": {
       "type": "AzureADandPersonalMicrosoftAccount"
      }
    }
  ]
}
```

## Configuration Properties

### General

| Property | Data Type | Required | Notes |
| --- | --- | --- | --- |
| client\_id | String | Yes | Your apps Client ID from [https://apps.dev.microsoft.com](https://apps.dev.microsoft.com) |
| redirect\_uri | String | Yes | Your apps Redirect URI from [https://apps.dev.microsoft.com](https://apps.dev.microsoft.com) |
| authorities | List<Authority> | No | The list of authorities your app needs |
| authorization\_user\_agent | AuthorizationAgent \(enum\) | No | Read more in the SSO wiki article, Options: DEFAULT, BROWSER, WEBVIEW |
| http | HttpConfiguration | No | HTTP configurations like timeout |
| logging | LoggingConfiguration | No | Level of detail logger captures, Optional configs: pii\_enabled \(boolean\), log\_level \([values](https://github.com/AzureAD/microsoft-authentication-library-for-android/blob/dev/msal/src/main/java/com/microsoft/identity/client/Logger.java#L81)\) |

### Authority Properties

| Property | Data Type | Required | Notes |
| --- | --- | --- | --- |
| type | String | Yes | Mirrors the audience or account type your app targets, Options: Microsoft Entra ID, B2C |
| audience | Object | No | Only applies to type=AAD, specifies the identity your app targets, mirror your app registration configuration |
| authority\_url | String | Yes | Required if and only if type=B2C, indicates the authority url or policy your app should use |
| default | boolean | Yes | If one or more authority is specified, a single default=true is required. |

### Audience Properties

| Property | Data Type | Required | Notes |
| --- | --- | --- | --- |
| type | String | Yes | Indicates the audience your app wants to target, Options: AzureADandPersonalMicrosoftAccount, PersonalMicrosoftAccount, AzureADMultipleOrgs, or AzureADMyOrg |
| tenant\_id | String | Yes | Required if and only if type=AzureADMyOrg. Optional for other type values. This can be a tenant domain \(e.g. contoso.com\) or a tenant ID \(e.g. aaaabbbb-0000-cccc-1111-dddd2222eeee\) |
