<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/angular/public-apis -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# Commonly used public APIs in MSAL Angular

Before you start here, make sure you understand how to [initialize the application object](https://learn.microsoft.com/en-us/entra/msal/javascript/angular/initialization).

The login APIs in MSAL retrieve an `authorization code` which can be exchanged for an [ID token](https://learn.microsoft.com/en-us/entra/identity-platform/id-tokens) for a signed in user, while consenting scopes for an additional resource, and an [access token](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens) containing the user consented scopes to allow your app to securely call the API. Learn more about [ID tokens](https://learn.microsoft.com/en-us/entra/identity-platform/id-tokens).

## Public APIs

`@azure/msal-angular` exposes the following, along with their configurations. See the [library references](https://azuread.github.io/microsoft-authentication-library-for-js/ref/modules/_azure_msal_angular.html) for properties and methods.

1. [`MsalService`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.service.ts/)
2. [`MsalGuard`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.guard.ts/)

   - [`MsalGuardConfiguration`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.guard.config.ts/)

3. [`MsalInterceptor`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.interceptor.ts/)

   - [`MsalInterceptorConfiguration`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.interceptor.config.ts/)

4. [`MsalBroadcastService`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.broadcast.service.ts/)
5. [`MsalModule`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.module.ts/)

The login and acquire token functions using Angular observables are found on the [IMsalService](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/IMsalService.ts/).

`@azure/msal-angular` also exposes the following:

1. [`MsalRedirectComponent`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.redirect.component.ts): Used for handling redirects. See the [redirect doc](https://learn.microsoft.com/en-us/entra/msal/javascript/angular/redirects) for more details.
2. [`MsalCustomNavigationClient`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular/src/msal.navigation.client.ts): Used for client-side navigation. See the [performance doc](https://learn.microsoft.com/en-us/entra/msal/javascript/angular/performance) for more details.

Additional functions from `@azure/msal-browser` are found on [`IPublicClientApplication`](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-browser/src/app/IPublicClientApplication.ts), with corresponding documentation [here](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-browser/docs/login-user.md).
