<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/ -->
<!-- Sitemap-Last-Modified: 2026-03-15 -->

# Microsoft Authentication Library for JavaScript \(MSAL.js\)

The Microsoft Authentication Library for JavaScript enables both client-side and server-side JavaScript applications to authenticate users using [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview) for work and school accounts, Microsoft personal accounts \(MSA\), and social identity providers like Facebook, Google, LinkedIn, Microsoft accounts, etc. through [Azure AD B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview#identity-providers) service. It also enables your app to get tokens to access [Microsoft Cloud](https://www.microsoft.com/enterprise) services such as [Microsoft Graph](https://graph.microsoft.com).

## Core and wrapper libraries

The [`lib`](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib) folder contains the source code for MSAL.js libraries in active development. You'll also find all the details about **installing the libraries** in their respective README.md files.

- [Microsoft Authentication Library for Node.js](https://learn.microsoft.com/en-us/entra/msal/javascript/node/initialize-public-client-application) \(v5.0.6\): A [Node.js](https://nodejs.org/en/) library that enables authentication and token acquisition with the Microsoft Identity platform in JavaScript applications. Implements the following OAuth 2.0 protocols and is [OpenID-compliant](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc). See the [source on GitHub](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node/).

  - [Authorization Code Grant](https://oauth.net/2/grant-types/authorization-code/) with [PKCE](https://oauth.net/2/pkce/)
  - [Device Code Grant](https://oauth.net/2/grant-types/device-code/)
  - [Refresh Token Grant](https://oauth.net/2/grant-types/refresh-token/)
  - [Client Credential Grant](https://oauth.net/2/grant-types/client-credentials/)
  - [Silent Flow](https://learn.microsoft.com/en-us/entra/identity-platform/msal-acquire-cache-tokens#acquiring-tokens-silently-from-the-cache)
  - [On-behalf-of Flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow)
  - [Interactive Flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow)
  - [Managed Identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)

- [Microsoft Authentication Library for JavaScript](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/about-msal-browser) \(v5.4.0\): A browser-based, framework-agnostic browser library that enables authentication and token acquisition with the Microsoft Identity platform in JavaScript applications. Implements the OAuth 2.0 [Authorization Code Flow with PKCE](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow), and is [OpenID-compliant](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc). See the [source on GitHub](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser/).
- **[Native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication) support in MSAL**: MSAL JS provides native authentication APIs that allow applications to implement a native experience with end-to-end customizable flows in their web applications. With native authentication, user can fully customize the user interface, including design elements, logo placement, and layout, ensuring a consistent and branded look. The native authentication feature is available for SPAs on [External ID for customers](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication)
- [Microsoft Authentication Library for React](https://learn.microsoft.com/en-us/entra/msal/javascript/react/getting-started) \(v5.0.6\): A wrapper of the msal-browser library for apps using React. See the [source on GitHub](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react/).
- [Microsoft Authentication Library for Angular](https://learn.microsoft.com/en-us/entra/msal/javascript/angular/initialization) \(v5.1.1\): A wrapper of the msal-browser library for apps using Angular framework. See the [source on GitHub](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-angular/).
- [Microsoft Authentication Extensions for Node](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/extensions/msal-node-extensions/): The Microsoft Authentication Extensions for Node offers secure mechanisms for client applications to perform cross-platform token cache serialization and persistence. It gives additional support to the Microsoft Authentication Library for Node \(MSAL\).

### What's new in v5

MSAL.js v5 introduces several key features:

- **Cross-Origin-Opener-Policy \(COOP\) support**: Enables popup authentication flows in environments with strict COOP headers.
- **Model Context Protocol \(MCP\) authentication**: Supports authentication flows for AI agent and tool integrations.
- **Nested App Authentication \(NAA\)**: Enables authentication for apps running inside Microsoft 365 host applications using `createNestablePublicClientApplication`.
- **localStorage AES-GCM encryption**: Encrypts the token cache in localStorage using AES-GCM for improved security.
- **Factory functions**: Use `createStandardPublicClientApplication` or `createNestablePublicClientApplication` to initialize MSAL with async configuration.
- **Platform broker \(WAM\) integration**: Enable Windows Authentication Manager \(WAM\) brokered authentication via the `allowPlatformBroker` configuration option.

For migration guides to MSAL JavaScript v5.x, see:

- [MSAL Browser v4 to v5 migration](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/v4-migration)
- [MSAL Node v3 to v5 migration](https://learn.microsoft.com/en-us/entra/msal/javascript/node/v5-migration)
- [MSAL Angular v4 to v5 upgrade](https://learn.microsoft.com/en-us/entra/msal/javascript/angular/v4-v5-upgrade-guide)
- [MSAL React migration guide](https://learn.microsoft.com/en-us/entra/msal/javascript/react/migration-guide)

### Libraries in Long-term Support \(LTS\)

The following table shows the active and LTS versions for each MSAL.js library:

| Library | Active version | LTS version |
| --- | --- | --- |
| msal-browser | v5.x | v2.x |
| msal-node | v5.x | v1.x |
| msal-react | v5.x | v1.x |
| msal-angular | v5.x | v2.x |

The LTS libraries, hosted on the [`msal-lts` branch](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/msal-lts), are no longer in active development but still receive critical security bug fix support.

Note

The `msal-lts` branch also includes v3.x and v4.x of msal-browser, which have transitioned out of active support.

- [Microsoft Authentication Library for JavaScript v2.x](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/msal-lts/lib/msal-browser)
- [Microsoft Authentication Library for Node.js v1.x](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/msal-lts/lib/msal-node)
- [Microsoft Authentication Library for React v1.x](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/msal-lts/lib/msal-react)
- [Microsoft Authentication Library for Angular v2.x](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/msal-lts/lib/msal-angular)

## Package structure

There are a number of different packages meant for different platforms. You can see the relationship between packages and different authentication flows they implement in the package structure below.

![Screenshot of the MSAL JavaScript package structure diagram.](https://learn.microsoft.com/en-us/entra/msal/javascript/media/packagestructure.png)

## Samples

The [`code samples`](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/samples) demonstrate usage of the Microsoft authentication libraries for JavaScript with the identity platform. Each code sample includes a `README.md` file describing how to build the project \(if applicable\) and run the sample application.

For a complete list of samples targeting JavaScript and other languages, frameworks, and platforms, please refer to the [Microsoft identity platform code samples](https://learn.microsoft.com/en-us/entra/identity-platform/sample-v2-code).

For native authentication features, the [sample apps](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples/tree/main/typescript/native-auth) demonstrate how to use native authentication in React and Angular web applications. Each code sample includes a `README.md` file describing how to build the project and run the sample application. Current native authentication API doesn't support Cross-Origin Resource Sharing \(CORS\), the sample app will run using local proxy.

## Package versioning

All of our libraries follow [semantic versioning](https://semver.org). We recommend using the latest version of each library to ensure you have the latest security patches and bug fixes.

## Security reporting

If you find a security issue with our libraries or services [please report it to the Microsoft Security Response Center \(MSRC\)](https://aka.ms/report-security-issue) with as much detail as possible.
