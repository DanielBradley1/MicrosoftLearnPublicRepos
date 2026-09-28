<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/support-fido2-authentication -->
<!-- Sitemap-Last-Modified: 2025-04-15 -->

# Support passwordless authentication with FIDO2 keys in apps you develop

These configurations and best practices will help you avoid common scenarios that block [FIDO2 passwordless authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2) from being available to users of your applications.

## General best practices

### Domain hints

Don't use a domain hint to bypass [home-realm discovery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/configure-authentication-for-federated-users-portal). This feature is meant to make sign-ins more streamlined, but the federated identity provider may not support passwordless authentication.

### Requiring specific credentials

If you are using SAML, do not specify that a password is required [using the RequestedAuthnContext element](https://learn.microsoft.com/en-us/entra/identity-platform/single-sign-on-saml-protocol#requestedauthncontext).

The RequestedAuthnContext element is optional, so to resolve this issue you can remove it from your SAML authentication requests. This is a general best practice, as using this element can also prevent other authentication options like multifactor authentication from working correctly.

### Using the most recently used authentication method

The sign-in method that was most recently used by a user will be presented to them first. This may cause confusion when users believe they must use the first option presented. However, they can choose another option by selecting "Other ways to sign in" as shown below.

![Image of the user authentication experience highlighting the button that allows the user to change the authentication method.](https://learn.microsoft.com/en-us/entra/identity-platform/media/support-fido2-authentication/most-recently-used-method.png)

## Platform-specific best practices

### Windows

The recommended options for implementing authentication are, in order:

- .NET desktop applications that are using the Microsoft Authentication Library \(MSAL\) should use the Windows Authentication Manager \(WAM\). This integration and its benefits are [documented on GitHub](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/wam).
- Use [WebView2](https://learn.microsoft.com/en-us/microsoft-edge/webview2/) to support FIDO2 in an embedded browser.
- Use the system browser. The MSAL libraries for desktop platforms use this method by default. You can consult our page on FIDO2 browser compatibility to ensure the browser you use supports FIDO2 authentication.

### Android

FIDO2 is supported for Android apps that use MSAL with [BROWSER as the authorization user agent](https://learn.microsoft.com/en-us/entra/msal/android/msal-configuration#authorization_user_agent) or broker integration. Broker is shipped in Microsoft Authenticator, Company Portal, or Link to Windows app on Android.

If you aren't using MSAL, you should still use the system web browser for authentication. Features such as SSO and Conditional Access rely on a shared web surface provided by the system web browser.

### iOS and macOS

FIDO2 is supported for iOS apps that use MSAL with either ASWebAuthenticationSession or broker integration. Broker is shipped in Microsoft Authenticator on iOS, and Microsoft Intune Company Portal on macOS.

Make sure that your network proxy doesn't block the associated domain validation by Apple. FIDO2 authentication requires Apple's associated domain validation to succeed, which requires certain Apple domains to be excluded from network proxies. For more information, see [Use Apple products on enterprise networks](https://support.apple.com/HT210060).

If you aren't using MSAL, you should still use the system web browser for authentication. Features such as SSO and Conditional Access rely on a shared web surface provided by the system web browser. For more information, see [Authenticating a User Through a Web Service \| Apple Developer Documentation](https://developer.apple.com/documentation/authenticationservices/authenticating_a_user_through_a_web_service).

### Web and single-page apps

The availability of FIDO2 passwordless authentication for applications that run in a web browser will depend on the combination of browser and platform. You can consult our [FIDO2 compatibility matrix](https://learn.microsoft.com/en-us/entra/identity/authentication/fido2-compatibility) to check if the combination your users will encounter is supported.

## Next steps

[Passkeys \(FIDO2\) authentication method in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2)
