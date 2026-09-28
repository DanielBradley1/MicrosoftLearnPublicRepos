<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/browser/migrate-spa-implicit-to-auth-code -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# Migrate a JavaScript single-page app from implicit grant to auth code flow

The Microsoft Authentication Library for JavaScript \(MSAL.js\) v2.0 brings support for the authorization code flow with PKCE and CORS to single-page applications on the Microsoft identity platform. Follow the steps in the sections below to migrate your MSAL.js 1.x application using the implicit grant to MSAL.js 2.0+ \(hereafter *2.x*\) and the authorization code flow with PKCE.

MSAL.js 2.x improves on MSAL.js 1.x by supporting the authorization code flow in the browser instead of the implicit grant flow. MSAL.js 2.x does **NOT** support the implicit flow.

## Migration steps

To update your application to MSAL.js 2.x and the auth code flow, there are three primary steps:

1. Switch your [app registration](#switch-redirect-uris-to-spa-platform) redirect URI\(s\) from **Web** platform to **Single-page application** platform.
2. Update your [code](#switch-redirect-uris-to-spa-platform) from MSAL.js 1.x to **2.x**.
3. Disable the [implicit grant](#disable-implicit-grant-settings) in your app registration when all applications sharing the registration have been updated to MSAL.js 2.x and the auth code flow with PKCE.

The following sections describe each step in additional detail.

## Switch redirect URIs to SPA platform

Tip

Steps in this article may vary slightly based on the portal you start from.

If you'd like to continue using your existing app registration for your applications, use the Microsoft Entra admin center to update the registration's redirect URIs to the SPA platform. Doing so enables the authorization code flow with PKCE and CORS support for apps that use the registration \(you still need to update your application's code to MSAL.js v2.x\).

Follow these steps for app registrations that are currently configured with **Web** platform redirect URIs:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Identity** > **Applications** > **App registrations**, select your application, and then **Authentication**.
3. In the **Web** platform tile under **Redirect URIs**, select the warning banner indicating that you should migrate your URIs.
4. Select *only* those redirect URIs whose applications will use MSAL.js 2.x, and then select **Configure**.

These redirect URIs should now appear in the **Single-page application** platform tile, showing that CORS support with the authorization code flow and PKCE is enabled for these URIs.

You can also [create a new app registration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-registration) instead of updating the redirect URIs in your existing registration.

## Update your code to MSAL.js 2.x

In MSAL 1.x, you created a application instance by initializing a UserAgentApplication as follows:

```javascript
// MSAL 1.x
import * as msal from "msal";

const msalInstance = new msal.UserAgentApplication(config);
```

In MSAL 2.x, initialize instead a \[PublicClientApplication\]\[msal-js-publicclientapplication\]:

```javascript
// MSAL 2.x
import * as msal from "@azure/msal-browser";

const msalInstance = new msal.PublicClientApplication(config);
```

For a full walk-through of adding MSAL 2.x to your application, see [Tutorial: Sign in users and call the Microsoft Graph API from a JavaScript single-page app \(SPA\) using auth code flow](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-javascript-auth-code).

For additional changes you might need to make to your code, see the [migration guide](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/v1-migration) on GitHub.

## Disable implicit grant settings

Once you've updated all your production applications that use this app registration and its client ID to MSAL 2.x and the authorization code flow, you should uncheck the implicit grant settings under the **Authentication** menu of the app registration.

When you uncheck the implicit grant settings in the app registration, the implicit flow is disabled for all applications using registration and its client ID.

**Do not** disable the implicit grant flow before you've updated all your applications to MSAL.js 2.x and the \[PublicClientApplication\]\[msal-js-publicclientapplication\].

## Next steps

To learn more about the authorization code flow, including the differences between the implicit and auth code flows, see the [Microsoft identity platform and OAuth 2.0 authorization code flow](https://learn.microsoft.com/en-us/entra/identity-pltform/v2-oauth2-auth-code-flow).

If you'd like to dive deeper into JavaScript single-page application development on the Microsoft identity platform, the multi-part [Scenario: Single-page application](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-overview) series of articles can help you get started.
