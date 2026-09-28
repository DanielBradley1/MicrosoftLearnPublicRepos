<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/msal-b2c-overview -->
<!-- Sitemap-Last-Modified: 2025-10-02 -->

# Use the Microsoft Authentication Library for JavaScript to work with Azure AD B2C

Important

Effective May 1, 2025, Azure Active Directory B2C \(Azure AD B2C\) is no longer available for new customers to purchase. To learn more, see [Is Azure AD B2C still available to purchase?](https://learn.microsoft.com/en-us/azure/active-directory-b2c/faq?tabs=app-reg-ga#azure-ad-b2c-end-of-sale) in our FAQ.

The [Microsoft Authentication Library for JavaScript \(MSAL.js\)](https://github.com/AzureAD/microsoft-authentication-library-for-js) enables JavaScript developers to authenticate users with social and local identities using [Azure Active Directory B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/overview) \(Azure AD B2C\).

By using Azure AD B2C as an identity management service, you can customize and control how your customers sign up, sign in, and manage their profiles when they use your applications.

Azure AD B2C also enables you to brand and customize the UI that your application displays during the authentication process.

## Supported app types and scenarios

MSAL.js enables [single-page applications](https://learn.microsoft.com/en-us/azure/active-directory-b2c/application-types#single-page-applications) to sign-in users with Azure AD B2C using the [authorization code flow with PKCE](https://learn.microsoft.com/en-us/azure/active-directory-b2c/authorization-code-flow) grant. With MSAL.js and Azure AD B2C:

- Users **can** authenticate with their social and local identities.
- Users **can** be authorized to access Azure AD B2C protected resources \(but not Microsoft Entra protected resources\).
- Users **cannot** obtain tokens for Microsoft APIs \(for example, MS Graph API\) using [delegated permissions](https://learn.microsoft.com/en-us/entra/identity-platform/permissions-consent-overview#types-of-permissions).
- Users with administrator privileges **can** obtain tokens for Microsoft APIs \(for example, MS Graph API\) using [delegated permissions](https://learn.microsoft.com/en-us/entra/identity-platform/permissions-consent-overview#types-of-permissions).

For more information, see: [Working with Azure AD B2C](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-browser/docs/working-with-b2c.md)

## Next steps

Follow the tutorial on how to:

- [Sign in users with Azure AD B2C in a single-page application](https://learn.microsoft.com/en-us/azure/active-directory-b2c/configure-authentication-sample-spa-app)
- [Call an Azure AD B2C protected web API](https://learn.microsoft.com/en-us/azure/active-directory-b2c/enable-authentication-web-api)
