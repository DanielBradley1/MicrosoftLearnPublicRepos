<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview -->
<!-- Sitemap-Last-Modified: 2025-02-18 -->

# Increase the resilience of authentication and authorization applications you develop

The [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview) helps you build applications your users and customers can sign in to using their Microsoft identities or social accounts. The Microsoft identity platform uses token-based authentication and authorization flows to communicate with applications. Client applications acquire tokens from an identity provider \(IdP\), Microsoft Entra and Azure AD B2C, to authenticate users and authorize applications to call protected APIs. A service validates tokens. For more information, see [Security tokens](https://learn.microsoft.com/en-us/entra/identity-platform/security-tokens).

A token is valid for a length of time, and then the app must acquire a new one. Rarely, a call to retrieve a token fails due to network or infrastructure issues or an authentication service outage. The [backup authentication system](https://learn.microsoft.com/en-us/entra/architecture/backup-authentication-system) increases authentication resilience if there's an outage. This system transparently and automatically handles authentications for supported applications and services if the primary Microsoft Entra service is unavailable or degraded.

The following articles have guidance for client and service applications for a signed in user and daemon applications. They contain best practices for using tokens and calling resources.

- [Increase the resilience of authentication and authorization in client applications you develop](https://learn.microsoft.com/en-us/entra/architecture/resilience-client-app)
- [Increase the resilience of authentication and authorization in daemon applications you develop](https://learn.microsoft.com/en-us/entra/architecture/resilience-daemon-app)
- [Build resilience in your identity and access management infrastructure](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-infrastructure)
- [Build resilience in your customer identity and access management with Azure AD B2C](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)
- [Building application support for the backup authentication system](https://learn.microsoft.com/en-us/entra/architecture/backup-authentication-system-apps)
- [Build services that are resilient to Microsoft Entra ID OpenID Connect metadata refresh](https://learn.microsoft.com/en-us/entra/identity-platform/howto-build-services-resilient-to-metadata-refresh)
