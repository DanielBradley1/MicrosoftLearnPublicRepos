<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview -->
<!-- Sitemap-Last-Modified: 2024-11-21 -->

# Overview of the Microsoft Authentication Library \(MSAL\)

The Microsoft Authentication Library \(MSAL\) enables developers to acquire [security tokens](https://learn.microsoft.com/en-us/entra/identity-platform/developer-glossary#security-token) from the Microsoft identity platform to authenticate users and access secured web APIs. It can be used to provide secure access to Microsoft Graph, other Microsoft APIs, third-party web APIs, or your own web API. MSAL supports many different application architectures and platforms including .NET, JavaScript, Java, Python, Android, and iOS.

MSAL provides multiple ways to get security tokens, with a consistent API for many platforms. Using MSAL provides the following benefits:

- There's no need to directly use the OAuth libraries or code against the protocol in your application.
- Can acquire tokens on behalf of a user or application \(when applicable to the platform\).
- Maintains a token cache for you and handles token refreshes when they're close to expiring.
- Helps you specify which audience you want your application to sign in. The sign in audience can include personal Microsoft accounts, social identities with Microsoft Entra External ID, work, school, or users in sovereign and national clouds.
- Helps you set up your application from configuration files.
- Helps you troubleshoot your app by exposing actionable exceptions, logging, and telemetry.

<iframe src="https://www.youtube-nocookie.com/embed/zufQ0QRUHUk" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

| Application types and scenarios | Tutorials |
| --- | --- |
| Single-page apps \(JavaScript\) | [Tutorial: Sign-in users to a React Single-page application \(SPA\)](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app) |
| Web applications | [Tutorial: Sign-in users to a ASP.NET Core Web application](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-prepare-app) |
| Web APIs | [Tutorial: Implement a protected endpoint a ASP.NET Core API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-api-dotnet-register-app) |
| Mobile and native applications | [Mobile application calling a web API on behalf of the user who's signed-in interactively](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-mobile-app-configuration). |
| Daemons and server-side applications | [Desktop/service daemon application calling web API on behalf of itself](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-app-configuration) |

## MSAL Languages and Frameworks

You can refer to the following documentation to learn more about the different MSAL libraries.

| MSAL Documentation | MSAL Library | Supported platforms and frameworks |
| --- | --- | --- |
| [MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/) | [MSAL.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) | .NET Framework, .NET, .NET MAUI, WINUI |
| [MSAL for Android](https://github.com/AzureAD/microsoft-authentication-library-for-android/tree/dev/docs) | [MSAL for Android](https://github.com/AzureAD/microsoft-authentication-library-for-android) | Android |
| [MSAL Angular](https://learn.microsoft.com/en-us/javascript/api/@azure/msal-angular/) | [MSAL Angular](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-angular) | Single-page apps with Angular and Angular.js frameworks |
| [MSAL for iOS and macOS](https://github.com/AzureAD/microsoft-authentication-library-for-objc/tree/dev/docs) | [MSAL for iOS and macOS](https://github.com/AzureAD/microsoft-authentication-library-for-objc) | iOS and macOS |
| [MSAL Java](https://learn.microsoft.com/en-us/entra/msal/java/) | [MSAL Java](https://github.com/AzureAD/microsoft-authentication-library-for-java) | Windows, macOS, Linux |
| [MSAL.js](https://learn.microsoft.com/en-us/javascript/api/overview/msal-overview) | [MSAL.js](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser) | JavaScript/TypeScript frameworks such as Vue.js, Ember.js, or Durandal.js |
| [MSAL Node](https://learn.microsoft.com/en-us/javascript/api/%40azure/msal-node/) | [MSAL Node](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node) | Web apps with Express, desktop apps with Electron, Cross-platform console apps |
| [MSAL Python](https://learn.microsoft.com/en-us/entra/msal/python/) | [MSAL Python](https://github.com/AzureAD/microsoft-authentication-library-for-python) | Windows, macOS, Linux |
| [MSAL React](https://learn.microsoft.com/en-us/javascript/api/%40azure/msal-react/) | [MSAL React](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react) | Single-page apps with React and React-based libraries \(Next.js, Gatsby.js\) |
| [MSAL Go \(Preview\)](https://learn.microsoft.com/en-us/entra/msal/go/) | [MSAL Go \(Preview\)](https://github.com/AzureAD/microsoft-authentication-library-for-go) | Windows, macOS, Linux |

Important

Active Directory Authentication Library \(ADAL\) has ended support. Customers need to ensure their applications are migrated to MSAL. MSAL integrates with the Microsoft identity platform \(v2.0\) endpoint, which is the unification of Microsoft personal accounts and work accounts into a single authentication system. ADAL integrates with a v1.0 endpoint which doesn't support personal accounts.

## Related content

- [Migrate applications to the Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-migration)
