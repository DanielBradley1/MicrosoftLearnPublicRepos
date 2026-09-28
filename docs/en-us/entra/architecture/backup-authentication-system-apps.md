<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/backup-authentication-system-apps -->
<!-- Sitemap-Last-Modified: 2025-07-22 -->

# Application requirements for the backup authentication system

The Microsoft Entra backup authentication system provides resilience to applications that use supported protocols and flows. For more information about the backup authentication system, see [Microsoft Entra ID's backup authentication system](https://learn.microsoft.com/en-us/entra/architecture/backup-authentication-system).

## Application requirements for protection

Applications must communicate with a supported hostname for the given Azure environment and use protocols currently supported by the backup authentication system. Use of authentication libraries, such as the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview), ensures that you're using authentication protocols supported by the backup authentication system.

### Hostnames supported by the backup authentication system

| Azure environment | Supported hostname |
| --- | --- |
| Azure Commercial | login.microsoftonline.com |
| Azure Government | login.microsoftonline.us |

### Authentication protocols supported by the backup authentication system

#### OAuth 2.0 and OpenID Connect \(OIDC\)

##### Common guidance

All applications using the Open Authorization \(OAuth\) 2.0 or OIDC protocols should adhere to the following practices to ensure resilience:

- Your application uses MSAL or strictly adheres to the OpenID Connect & OAuth2 specifications. Microsoft recommends using MSAL libraries appropriate to your platform and use case. Using these libraries ensures the use of APIs and call patterns are supportable by the backup authentication system.
- Your application uses a fixed set of scopes instead of [dynamic consent](https://learn.microsoft.com/en-us/entra/identity-platform/scopes-oidc) when acquiring access tokens.
- Your application doesn't use the [Resource Owner Password Credentials Grant](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth-ropc). **This grant type won't be supported** by the backup authentication system for any client type. Microsoft strongly recommends switching to alternative grant flows for better security and resilience.
- Your application doesn't rely upon the [UserInfo endpoint](https://learn.microsoft.com/en-us/entra/identity-platform/userinfo). Switching to using an ID token instead reduces latency by eliminating up to two network requests, and use existing support for ID token resilience within the backup authentication system.

##### Native applications

Native applications are public client applications that run directly on desktop or mobile devices and not in a web browser. They're registered as public clients in their application registration on the Microsoft Entra admin center or Azure portal.

Native applications are protected by the backup authentication system when all the following are true:

1. Your application persists the token cache for at least three days. Applications should use the device's token cache location or the [token cache serialization API](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization) to persist the token cache even when the user closes the application.
2. Your application makes use of the MSAL [AcquireTokenSilent API](https://learn.microsoft.com/en-us/entra/msal/dotnet/acquiring-tokens/acquire-token-silently) to retrieve tokens using cached Refresh Tokens. The use of the [AcquireTokenInteractive API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token-interactive) might fail to acquire a token from the backup authentication system if user interaction is required.

The backup authentication system doesn't currently support the [device authorization grant](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-device-code).

##### Single-page web applications

Single-page web applications \(SPAs\) have limited support in the backup authentication system. SPAs that use the [implicit grant flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-implicit-grant-flow) and request only OpenID Connect ID tokens are protected. Only apps that either use MSAL.js 1.x or implement the implicit grant flow directly can use this protection, as MSAL.js 2.x doesn't support the implicit flow.

The backup authentication system doesn't currently support the [authorization code flow with Proof Key for Code Exchange](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow).

##### Web applications and services

The backup authentication system doesn't currently support web applications and services that are configured as confidential clients. Protection for the [authorization code grant flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) and subsequent token acquisition using refresh tokens and client secrets or [certificate credentials](https://learn.microsoft.com/en-us/entra/identity-platform/certificate-credentials) isn't currently supported. The OAuth 2.0 [on-behalf-of flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow) isn't currently supported.

#### SAML 2.0 single sign-on \(SSO\)

The backup authentication system partially supports the Security Assertion Markup Language \(SAML\) 2.0 single sign-on \(SSO\) protocol. Flows that use the SAML 2.0 Identity Provider \(IdP\) Initiated flow are protected by the backup authentication system. Applications that use the [Service Provider \(SP\) Initiated flow](https://learn.microsoft.com/en-us/entra/identity-platform/single-sign-on-saml-protocol), aren't currently protected by the backup authentication system.

### Workload identity authentication protocols supported by the backup authentication system

#### OAuth 2.0

##### Managed identity

Applications that use Managed Identities to acquire Microsoft Entra access tokens are protected. Microsoft recommends the use of user-assigned managed identities in most scenarios. This protection applies to both [user and system-assigned managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

##### Service principal

The backup authentication system doesn't currently support service principal-based Workload identity authentication using the [client credentials grant flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow). Microsoft recommends using the version of MSAL appropriate to your platform so your application is protected by the backup authentication system when the protection becomes available.

## Next steps

- [Microsoft Entra ID's backup authentication system](https://learn.microsoft.com/en-us/entra/architecture/backup-authentication-system)
- [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview)
- [Introduction to the backup authentication system](https://azure.microsoft.com/blog/advancing-service-resilience-in-azure-active-directory-with-its-backup-authentication-service/)
- [Resilience Defaults for Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/resilience-defaults)
