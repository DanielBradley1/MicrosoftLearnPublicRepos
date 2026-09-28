<!-- Source: https://learn.microsoft.com/en-us/entra/msal/overview -->
<!-- Sitemap-Last-Modified: 2024-02-09 -->

# Overview of the Microsoft Authentication Library \(MSAL\)

The Microsoft Authentication Library \(MSAL\) enables developers to acquire security tokens from the Microsoft identity platform to authenticate users and access secured web APIs. It can be used to provide secure access to Microsoft Graph, Microsoft APIs, third-party web APIs, or your own web API. MSAL supports different application architectures and platforms, including .NET, JavaScript, Java, Python, Android, and iOS.

MSAL is a token acquisition library that offers several ways to get tokens, with a consistent API for supported platforms. Using MSAL provides the following benefits:

- No need to directly write applications against the OAuth protocol. The plumbing is handled by the library.
- Can acquire tokens on behalf of a user or application \(when applicable to the platform\).
- The library maintains a token cache and refreshes tokens for you when they're about to expire. You don't need to handle token expiration on your own.
- Helps you specify which audience you want your application to sign in. The sign in audience can include personal Microsoft accounts, social identities with Microsoft Entra External ID organizations, work, school, or users in sovereign and national clouds.
- Helps you set up your application from configuration files.
- Helps you troubleshoot your app by exposing actionable exceptions, logging, and telemetry.

<iframe src="https://www.youtube-nocookie.com/embed/zufQ0QRUHUk" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Application types and scenarios

Using MSAL, a token can be acquired for many application types: web applications, web APIs, single-page apps \(JavaScript\), mobile and native applications, as well as daemons and server-side applications.

MSAL can be used in several application scenarios, including the following:

- Single page applications \(JavaScript\)
- Web application signing in users
- Web application signing in a user and calling a web API on behalf of the user
- Web API authentication, ensuring that only authenticated users can access it
- Web API calling another downstream web API on behalf of the signed-in user
- Desktop application calling a web API on behalf of the signed-in user
- Mobile application calling a web API on behalf of the user who's signed-in interactively
- Desktop/service daemon application calling web API on behalf of itself

## Languages and frameworks

| Library | Supported platforms and frameworks |
| :--- | :--- |
| [MSAL.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) | .NET Framework, .NET, Universal Windows Platform |
| [MSAL Java](https://github.com/AzureAD/microsoft-authentication-library-for-java) | Windows, macOS, Linux |
| [MSAL Python](https://github.com/AzureAD/microsoft-authentication-library-for-python) | Windows, macOS, Linux |
| [MSAL.js](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser) | JavaScript/TypeScript frameworks such as Vue.js, Ember.js, or Durandal.js |
| [MSAL Node](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node) | Web apps with Express, desktop apps with Electron, Cross-platform console apps |
| [MSAL React](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react) | Single-page apps with React and React-based libraries \(Next.js, Gatsby.js\) |
| [MSAL Angular](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-angular) | Single-page apps with Angular and Angular.js frameworks |
| [MSAL for Android](https://github.com/AzureAD/microsoft-authentication-library-for-android) | Android |
| [MSAL for iOS and macOS](https://github.com/AzureAD/microsoft-authentication-library-for-objc) | iOS and macOS |
| [MSAL Go](https://github.com/AzureAD/microsoft-authentication-library-for-go) | Windows, macOS, Linux |
