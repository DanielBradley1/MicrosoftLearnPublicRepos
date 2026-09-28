<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/authentication-flows-app-scenarios -->
<!-- Sitemap-Last-Modified: 2025-04-14 -->

# Microsoft identity platform app types and authentication flows

The Microsoft identity platform supports authentication for different kinds of modern application architectures. All of the architectures are based on the industry-standard protocols [OAuth 2.0 and OpenID Connect](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols). By using the [authentication libraries for the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/reference-v2-libraries), applications authenticate identities and acquire tokens to access protected APIs.

This article describes authentication flows and the application scenarios that they're used in.

## Application categories

[Security tokens](https://learn.microsoft.com/en-us/entra/identity-platform/security-tokens) can be acquired from several types of applications, including:

- Web apps
- Mobile apps
- Desktop apps
- Web APIs

Tokens can also be acquired by apps running on devices that don't have a browser or are running on the Internet of Things \(IoT\).

The following sections describe the categories of applications.

### Protected resources vs. client applications

Authentication scenarios involve two activities:

- **Acquiring security tokens for a protected web API**: We recommend that you use the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview), developed and supported by Microsoft.
- **Protecting a web API or a web app**: One challenge of protecting these resources is validating the security token. On some platforms, Microsoft offers [middleware libraries](https://learn.microsoft.com/en-us/entra/identity-platform/reference-v2-libraries).

### With users or without users

Most authentication scenarios acquire tokens on behalf of signed-in users.

![Scenarios with users](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/scenarios-with-users.svg)

However, there are also daemon apps. In these scenarios, applications acquire tokens on behalf of themselves with no user.

![Scenarios with daemon apps](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/daemon-app.svg)

### Single-page, public client, and confidential client applications

Security tokens can be acquired by multiple types of applications. These applications tend to be separated into the following three categories. Each is used with different libraries and objects.

- **Single-page applications**: Also known as SPAs, these are web apps in which tokens are acquired by a JavaScript or TypeScript app running in the browser. Many modern apps have a single-page application at the front end that's primarily written in JavaScript. The application often uses a framework like Angular, React, or Vue. MSAL.js is the only Microsoft Authentication Library that supports single-page applications.
- **Public client applications**: Apps in this category, like the following types, always sign in users:

  - Desktop apps that call web APIs on behalf of signed-in users
  - Mobile apps
  - Apps running on devices that don't have a browser, like those running on IoT

- **Confidential client applications**: Apps in this category include:

  - Web apps that call a web API
  - Web APIs that call a web API
  - Daemon apps, even when implemented as a console service like a Linux daemon or a Windows service

### Sign-in audience

The available authentication flows differ depending on the sign-in audience. Some flows are available only for work or school accounts. Others are available both for work or school accounts and for personal Microsoft accounts.

For more information, see [Supported account types](https://learn.microsoft.com/en-us/entra/identity-platform/v2-supported-account-types#account-type-support-in-authentication-flows).

## Application types

The Microsoft identity platform supports authentication for these app architectures:

- Single-page apps
- Web apps
- Web APIs
- Mobile apps
- Native apps
- Daemon apps
- Server-side apps

Applications use the different authentication flows to sign in users and get tokens to call protected APIs.

### Single-page application

Many modern web apps are built as client-side single-page applications. These applications use JavaScript or a framework like Angular, Vue, and React. These applications run in a web browser.

Single-page applications differ from traditional server-side web apps in terms of authentication characteristics. By using the Microsoft identity platform, single-page applications can sign in users and get tokens to access back-end services or web APIs. The Microsoft identity platform offers two grant types for JavaScript applications:

| MSAL.js \(2.x\) | MSAL.js \(1.x\) |
| --- | --- |
| ![A single-page application auth](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/spa-app-auth.svg) | ![A single-page application implicit](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/spa-app.svg) |

### Web app that signs in a user

![A web app that signs in a user](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/scenario-webapp-signs-in-users.svg)

To help protect a web app that signs in a user:

- If you develop in .NET, you use ASP.NET or ASP.NET Core with the ASP.NET OpenID Connect middleware. Protecting a resource involves validating the security token, which is done by the [IdentityModel extensions for .NET](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki) and not MSAL libraries.
- If you develop in Node.js, you use [MSAL Node](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node).

For more information, see [Sign in users in a sample web app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in).

### Web app that signs in a user and calls a web API on behalf of the user

![A web app calling web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/web-app.svg)

To call a web API from a web app on behalf of a user, use the authorization code flow and store the acquired tokens in the token cache. When needed, MSAL refreshes tokens and the controller silently acquires tokens from the cache.

For more information, see [Web app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration).

### Desktop app that calls a web API on behalf of a signed-in user

For a desktop app to call a web API that signs in users, use the interactive token-acquisition methods of MSAL. With these interactive methods, you can control the sign-in UI experience. MSAL uses a web browser for this interaction.

![A desktop app calling a web API](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/desktop-app.svg)

There's another possibility for Windows-hosted applications on computers joined either to a Windows domain or by Microsoft Entra ID. These applications can silently acquire a token by using [integrated Windows authentication](https://aka.ms/msal-net-iwa).

Applications running on a device without a browser can still call an API on behalf of a user. To authenticate, the user must sign in on another device that has a web browser. This scenario requires that you use the [device code flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-device-code).

![Device code flow](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/device-code-flow-app.svg)

Though we don't recommend that you use it, the [username/password flow](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token-username-password) is available in public client applications. This flow is still needed in some scenarios like DevOps.

Using the username/password flow constrains your applications and is no longer considered secure. For instance, applications can't sign in a user who needs to use multifactor authentication or the Conditional Access tool in Microsoft Entra ID. Your applications also don't benefit from single sign-on. Authentication with the username/password flow goes against the principles of modern authentication and is provided only for legacy reasons.

In desktop apps, if you want the token cache to persist, you can customize the [token cache serialization](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization). By implementing dual token cache serialization, you can use backward-compatible and forward-compatible token caches.

For more information, see [Desktop app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-app-configuration).

### Mobile app that calls a web API on behalf of an interactive user

Similar to a desktop app, a mobile app calls the interactive token-acquisition methods of MSAL to acquire a token for calling a web API.

![A mobile app calling a web API](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/mobile-app.svg)

MSAL iOS and MSAL Android use the system web browser by default. However, you can direct them to use the embedded web view instead. There are specificities that depend on the mobile platform: iOS, or Android.

Some scenarios, like those that involve Conditional Access related to a device ID or a device enrollment, require a broker to be installed on the device. Examples of brokers are Microsoft Company Portal on Android and Microsoft Authenticator on Android and iOS.

For more information, see [Mobile app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-mobile-app-configuration).

Note

A mobile app that uses MSAL iOS or MSAL Android can have app protection policies applied to it. For instance, the policies might prevent a user from copying protected text. The mobile app is managed by Intune and is recognized by Intune as a managed app. For more information, see [Microsoft Intune App SDK overview](https://learn.microsoft.com/en-us/mem/intune/developer/app-sdk).

The [Intune App SDK](https://learn.microsoft.com/en-us/mem/intune/developer/app-sdk-get-started) is separate from MSAL libraries and interacts with Microsoft Entra ID on its own.

### Protected web API

You can use the Microsoft identity platform endpoint to secure web services like your app's RESTful API. A protected web API is called through an access token. The token helps secure the API's data and authenticate incoming requests. The caller of a web API appends an access token in the authorization header of an HTTP request.

If you want to protect your ASP.NET or ASP.NET Core web API, validate the access token. For this validation, you use the ASP.NET JWT middleware. The validation is done by the [IdentityModel extensions for .NET](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki) library and not by MSAL.NET.

For more information, see [Protected web API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-protected-web-api-expose-scopes).

### Web API that calls another web API on behalf of a user

For your protected web API to call another web API on behalf of a user, your app needs to acquire a token for the downstream web API. Such calls are sometimes referred to as *service-to-service* calls. Web APIs that call other web APIs need to provide custom cache serialization.

![A web API calling another web API](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/web-api.svg)

For more information, see [Web API that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration).

### Daemon app that calls a web API in the daemon's name

Apps that have long-running processes or that operate without user interaction also need a way to access secure web APIs. Such an app can authenticate and get tokens by using the app's identity. The app proves its identity by using a client secret or certificate.

You can write such daemon apps that acquire a token for the calling app by using the [client credential](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-acquire-token#acquiretokenforclient-api) acquisition methods in MSAL. These methods require a client secret that you add to the app registration in Microsoft Entra ID. The app then shares the secret with the called daemon. Examples of such secrets include application passwords, certificate assertion, and client assertion.

![A daemon app called by other apps and APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/daemon-app.svg)

For more information, see [Daemon application that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-app-configuration).

## Scenarios and supported authentication flows

You use authentication flows to implement the application scenarios that are requesting tokens. There isn't a one-to-one mapping between application scenarios and authentication flows.

Scenarios that involve acquiring tokens also map to OAuth 2.0 authentication flows. For more information, see [OAuth 2.0 and OpenID Connect protocols on the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols).

| Scenario | Detailed scenario walk-through | OAuth 2.0 flow and grant | Audience |
| --- | --- | --- | --- |
| [![Single-Page App with Auth code](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/spa-app-auth.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration) | [Single-page app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration) | [Authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) with PKCE | Work or school accounts, personal accounts, and Azure Active Directory B2C \(Azure AD B2C\) |
| [![Single-Page App with Implicit](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/spa-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration) | [Single-page app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration) | [Implicit](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-implicit-grant-flow) | Work or school accounts, personal accounts, and Azure Active Directory B2C \(Azure AD B2C\) |
| [![Web app that signs in users](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/scenario-webapp-signs-in-users.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in) | [Web app that signs in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in) | [Authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) | Work or school accounts, personal accounts, and Azure AD B2C |
| [![Web app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/web-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration) | [Web app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-app-configuration) | [Authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) | Work or school accounts, personal accounts, and Azure AD B2C |
| [![Desktop app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/desktop-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-app-configuration) | [Desktop app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-app-configuration) | Interactive by using [authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) with PKCE | Work or school accounts, personal accounts, and Azure AD B2C |
|  |  | Integrated Windows authentication | Work or school accounts |
|  |  | [Resource owner password](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth-ropc) | Work or school accounts and Azure AD B2C |
| [![Browserless application](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/device-code-flow-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token-device-code-flow) | [Browserless app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token-device-code-flow) | [Device code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-device-code) | Work or school accounts, personal accounts, but not Azure AD B2C |
| [![Mobile app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/mobile-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-mobile-app-configuration) | [Mobile app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-mobile-app-configuration) | Interactive by using [authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) with PKCE | Work or school accounts, personal accounts, and Azure AD B2C |
|  |  | [Resource owner password](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth-ropc) | Work or school accounts and Azure AD B2C |
| [![Daemon app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/daemon-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-app-configuration) | [Daemon app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-app-configuration) | [Client credentials](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow) | App-only permissions that have no user and are used only in Microsoft Entra organizations |
| [![Web API that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/web-api.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration) | [Web API that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration) | [On-behalf-of](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow) | Work or school accounts and personal accounts |

## Scenarios and supported platforms and languages

Microsoft Authentication Libraries support multiple platforms:

- .NET
- .NET Framework
- Java
- JavaScript
- macOS
- Native Android
- Native iOS
- Node.js
- Python

You can also use various languages to build your applications.

In the Windows column of the following table, each time .NET is mentioned, .NET Framework is also possible. The latter is omitted to avoid cluttering the table.

| Scenario | Windows | Linux | Mac | iOS | Android |
| --- | --- | --- | --- | --- | --- |
| [Single-page app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration)  <br><br><br>[![Single-Page App Auth](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/spa-app-auth.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration) | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png) MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js |
| [Single-page app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration)  <br><br><br>[![Single-Page App Implicit](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/spa-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration) | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png) MSAL.js | ![MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_js.png)  <br>MSAL.js |
| [Web app that signs in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in)  <br><br><br>[![Web app that signs-in users](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/scenario-webapp-signs-in-users.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in) | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> |  |  |
| [Web app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration)  <br>  <br><br><br>[![Web app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/web-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration) | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core + MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>Flask + MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core + MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>Flask + MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core + MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>Flask + MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> |  |  |
| [Desktop app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-app-configuration)  <br>  <br><br><br>[![Desktop app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/desktop-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-app-configuration)<br><br>![Device code flow](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/device-code-flow-app.svg) | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python  <br>![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br>![iOS / Objective C or swift](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_ios.png) MSAL.objc |  |  |
| [Mobile app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-mobile-app-configuration)  <br><br><br>[![Mobile app that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/mobile-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-mobile-app-configuration) | ![UWP](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_windows.png) MSAL.NET |  |  | ![iOS / Objective C or swift](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_ios.png) MSAL.objc | ![Android](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_android.png) MSAL.Android |
| [Daemon app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-app-configuration)  <br><br><br>[![Daemon app](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/daemon-app.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-app-configuration) | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png) MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> |  |  |
| [Web API that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration)  <br>  <br><br><br>[![Web API that calls web APIs](https://learn.microsoft.com/en-us/entra/identity-platform/media/scenarios/web-api.svg)](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-api-call-api-app-configuration) | ![ASP.NET Core](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core + MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core + MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> | ![.NET](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_netcore.png)  <br>ASP.NET Core + MSAL.NET ![MSAL Java](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_java.png)  <br>MSAL Java  <br>![MSAL Python](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small_logo_python.png)  <br>MSAL Python ![MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-v2-code/small-logo-nodejs.png)  <br>MSAL Node  <br> |  |  |

For more information, see [Microsoft identity platform authentication libraries](https://learn.microsoft.com/en-us/entra/identity-platform/reference-v2-libraries).

## Next steps

For more information about authentication, see:

- [Authentication vs. authorization.](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-vs-authorization)
- [Microsoft identity platform access tokens.](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens)
- [Securing access to IoT apps.](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/iot#security)
