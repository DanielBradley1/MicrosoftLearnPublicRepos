<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/authentication-vs-authorization -->
<!-- Sitemap-Last-Modified: 2025-03-21 -->

# Authentication vs. authorization

This article defines authentication and authorization. It also briefly covers multifactor authentication and how you can use the Microsoft identity platform to authenticate and authorize users in your web apps, web APIs, or apps that call protected web APIs. If you see a term you aren't familiar with, try our [glossary](https://learn.microsoft.com/en-us/entra/identity-platform/developer-glossary) or our [Microsoft identity platform videos](https://learn.microsoft.com/en-us/entra/identity-platform/identity-videos), which cover basic concepts.

## Authentication

*Authentication* is the process of proving that you are who you say you are. This is achieved by verification of the identity of a person or device. It's sometimes shortened to *AuthN*. The Microsoft identity platform uses the [OpenID Connect](https://openid.net/connect/) protocol for handling authentication.

## Authorization

*Authorization* is the act of granting an authenticated party permission to do something. It specifies what data you're allowed to access and what you can do with that data. Authorization is sometimes shortened to *AuthZ*. The Microsoft identity platform provides resource owners the ability to use the [OAuth 2.0](https://oauth.net/2/) protocol for handling authorization, but the Microsoft cloud also has other authorization systems such as [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference), [Azure RBAC](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview), and [Exchange RBAC](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac).

## Multifactor authentication

*Multifactor authentication* is the act of providing another factor of authentication to an account. This is often used to protect against brute force attacks. It's sometimes shortened to *MFA* or *2FA*. The [Microsoft Authenticator](https://support.microsoft.com/account-billing/set-up-the-microsoft-authenticator-app-as-your-verification-method-33452159-6af9-438f-8f82-63ce94cf3d29) can be used as an app for handling two-factor authentication. For more information, see [multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks).

## Authentication and authorization using the Microsoft identity platform

Creating apps that each maintain their own username and password information incurs a high administrative burden when adding or removing users across multiple apps. Instead, your apps can delegate that responsibility to a centralized identity provider.

Microsoft Entra ID is a centralized identity provider in the cloud. Delegating authentication and authorization to it enables scenarios such as:

- Conditional Access policies that require a user to be in a specific location.
- Multifactor authentication which requires a user to have a specific device.
- Enabling a user to sign in once and then be automatically signed in to all of the web apps that share the same centralized directory. This capability is called *single sign-on \(SSO\)*.

The Microsoft identity platform simplifies authorization and authentication for application developers by providing identity as a service. It supports industry-standard protocols and open-source libraries for different platforms to help you start coding quickly. It allows developers to build applications that sign in all Microsoft identities, get tokens to call [Microsoft Graph](https://developer.microsoft.com/graph/), access Microsoft APIs, or access other APIs that developers have built.

This video explains the Microsoft identity platform and the basics of modern authentication:

<iframe src="https://www.youtube-nocookie.com/embed/tkQJSHFsduY" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Here's a comparison of the protocols that the Microsoft identity platform uses:

- **OAuth versus OpenID Connect**: The platform uses OAuth for authorization and OpenID Connect \(OIDC\) for authentication. OpenID Connect is built on top of OAuth 2.0, so the terminology and flow are similar between the two. You can even both authenticate a user \(through OpenID Connect\) and get authorization to access a protected resource that the user owns \(through OAuth 2.0\) in one request. For more information, see [OAuth 2.0 and OpenID Connect protocols](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols) and [OpenID Connect protocol](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc).
- **OAuth versus SAML**: The platform uses OAuth 2.0 for authorization and SAML for authentication. For more information on how to use these protocols together to both authenticate a user and get authorization to access a protected resource, see [Microsoft identity platform and OAuth 2.0 SAML bearer assertion flow](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-token-exchange-saml-oauth).
- **OpenID Connect versus SAML**: The platform uses both OpenID Connect and SAML to authenticate a user and enable single sign-on. SAML authentication is commonly used with identity providers such as Active Directory Federation Services \(AD FS\) federated to Microsoft Entra ID, so it's often used in enterprise applications. OpenID Connect is commonly used for apps that are purely in the cloud, such as mobile apps, websites, and web APIs.

## Related content

For other articles that cover authentication and authorization basics:

- To learn how access tokens, refresh tokens, and ID tokens are used in authorization and authentication, see [Security tokens](https://learn.microsoft.com/en-us/entra/identity-platform/security-tokens).
- To learn about the process of registering your application so it can integrate with the Microsoft identity platform, see [Application model](https://learn.microsoft.com/en-us/entra/identity-platform/application-model).
- To learn about proper authorization using token claims, see [Secure applications and APIs by validating claims](https://learn.microsoft.com/en-us/entra/identity-platform/claims-validation)
