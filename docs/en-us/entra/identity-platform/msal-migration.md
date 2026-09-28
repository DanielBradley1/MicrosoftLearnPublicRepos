<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/msal-migration -->
<!-- Sitemap-Last-Modified: 2025-02-28 -->

# Migrate applications to the Microsoft Authentication Library \(MSAL\)

If any of your applications use the Azure Active Directory Authentication Library \(ADAL\) for authentication and authorization capabilities, it's time to migrate them to the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/msal).

- All Microsoft support and development for ADAL, including security fixes, ended on June 30, 2023.
- There were no ADAL feature releases or new platform version releases planned before the deprecation date.
- No new features have been added to ADAL since June 30, 2020.

Warning

Azure Active Directory Authentication Library \(ADAL\) has been deprecated. While existing apps that use ADAL will continue to work, Microsoft will no longer release security fixes on ADAL. Use the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/msal/) to avoid putting your app's security at risk.

## Why switch to MSAL?

If you've developed apps using the Azure AD \(v1.0\) endpoint, you're likely using ADAL. Since Microsoft identity platform \(v2.0\) endpoint has changed significantly, the new library \(MSAL\) was entirely built for the new endpoint.

MSAL is designed to enable a secure solution without developers having to worry about the implementation details. It simplifies and manages acquiring, managing, caching, and refreshing tokens, and uses best practices for resilience. We recommend you use MSAL to [increase the resilience of authentication and authorization in client applications that you develop](https://learn.microsoft.com/en-us/entra/architecture/resilience-client-app?tabs=csharp#use-the-microsoft-authentication-library-msal).

MSAL provides multiple benefits over ADAL, including the following features:

| Features | MSAL | ADAL |
| --- | --- | --- |
| **Security** |  |  |
| Security fixes beyond June 2023 | ![Security fixes beyond June 2023 - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Security fixes beyond June 2023 - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Proactively refresh and revoke tokens based on policy or critical events for Microsoft Graph and other APIs that support [Continuous Access Evaluation \(CAE\)](https://learn.microsoft.com/en-us/entra/identity-platform/app-resilience-continuous-access-evaluation). | ![Proactively refresh and revoke tokens based on policy or critical events for Microsoft Graph and other APIs that support Continuous Access Evaluation \(CAE\) - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Proactively refresh and revoke tokens based on policy or critical events for Microsoft Graph and other APIs that support Continuous Access Evaluation \(CAE\) - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Standards compliant with OAuth v2.0 and OpenID Connect \(OIDC\) | ![Standards compliant with OAuth v2.0 and OpenID Connect \(OIDC\) - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Standards compliant with OAuth v2.0 and OpenID Connect \(OIDC\) - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| **User accounts and experiences** |  |  |
| Microsoft Entra accounts | ![Microsoft Entra accounts - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Microsoft Entra accounts - ADAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |
| Microsoft account \(MSA\) | ![Microsoft account \(MSA\) - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Microsoft account \(MSA\) - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Azure AD B2C accounts | ![Azure AD B2C accounts - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Azure AD B2C accounts - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Best single sign-on experience | ![Best single sign-on experience - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Best single sign-on experience - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| **Authentication experiences** |  |  |
| Continuous access evaluation through proactive token refresh | ![Proactive token renewal - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Proactive token renewal - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Throttling | ![Throttling - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Throttling - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Auth broker support | ![Device-based Conditional Access policy - MSAL has the feature built-in](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Device-based Conditional Access policy - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |
| Token protection | ![Token protection - MSAL provides the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Token protection - ADAL doesn't provide the feature](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) |

## Additional capabilities of MSAL over ADAL

- Proof of possession tokens
- Microsoft Entra certificate-based authentication \(CBA\) on mobile
- System browsers on mobile devices
- Where ADAL had only authentication context class, MSAL exposes the notion of a collection of client apps \(public client and confidential client\).

## Active Directory Federation Services \(AD FS\) support in MSAL

You can use MSAL.NET, MSAL Java, MSAL.js, and MSAL Python to get tokens from Active Directory Federation Services \(AD FS\) 2019 or later. Earlier versions of AD FS, including AD FS 2016, are unsupported by MSAL.

If you need to continue using AD FS, you should upgrade to AD FS 2019 or later before you update your applications from ADAL to MSAL.

## How to migrate to MSAL

Before you start the migration, you need to identify which of your apps are using ADAL for authentication. Follow the steps in this article to get a list by using the Azure portal:

- [How to: Get a complete list of apps using ADAL in your tenant](https://learn.microsoft.com/en-us/entra/identity-platform/howto-get-list-of-all-auth-library-apps)

After identifying applications that use ADAL, migrate them to MSAL depending on your app type:

**Single-page app \(SPA\)**

- [ADAL.js to MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/msal-compare-msal-js-and-adal-js)

**Web app**

- [ADAL Node to MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/msal-node-migration)
- [ADAL.NET to MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/msal-net-migration)

**Web API**

- [ADAL Java to MSAL Java](https://learn.microsoft.com/en-us/entra/msal/java/advanced/migrate-adal-msal-java)
- [ADAL Python to MSAL Python](https://learn.microsoft.com/en-us/entra/msal/python/advanced/migrate-python-adal-msal)
- [ADAL.NET to MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/msal-net-migration)

**Desktop app**

- [ADAL Java to MSAL Java](https://learn.microsoft.com/en-us/entra/msal/java/advanced/migrate-adal-msal-java)
- [ADAL Python to MSAL Python](https://learn.microsoft.com/en-us/entra/msal/python/advanced/migrate-python-adal-msal)
- [ADAL.NET to MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/msal-net-migration)

**Mobile app**

- [ADAL.Android to MSAL.Android](https://learn.microsoft.com/en-us/entra/identity-platform/migrate-android-adal-msal)
- [ADAL.iOS to MSAL.iOS](https://learn.microsoft.com/en-us/entra/msal/objc/migrate-objc-adal-msal)

**Service / daemon app**

- [ADAL Python to MSAL Python](https://learn.microsoft.com/en-us/entra/msal/python/advanced/migrate-python-adal-msal)
- [ADAL.NET to MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/msal-net-migration)
- [ADAL Node to MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/msal-node-migration)
- [ADAL Java to MSAL Java](https://learn.microsoft.com/en-us/entra/msal/java/advanced/migrate-adal-msal-java)

MSAL Supports a wide range of application types and scenarios. Refer to [Microsoft Authentication Library support for several application types](https://learn.microsoft.com/en-us/entra/identity-platform/reference-v2-libraries#single-page-application-spa).

ADAL to MSAL migration guide for different platforms are available in the following links:

- [Migrate to MSAL iOS and macOS](https://learn.microsoft.com/en-us/entra/msal/objc/migrate-objc-adal-msal)
- [Migrate to MSAL Java](https://learn.microsoft.com/en-us/entra/msal/java/advanced/migrate-adal-msal-java)
- [Migrate to MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/msal-compare-msal-js-and-adal-js)
- [Migrate to MSAL .NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/msal-net-migration)
- [Migrate to MSAL Node](https://learn.microsoft.com/en-us/entra/identity-platform/msal-node-migration)
- [Migrate to MSAL Python](https://learn.microsoft.com/en-us/entra/msal/python/advanced/migrate-python-adal-msal)

## Migration help

If you have questions about migrating your app from ADAL to MSAL, here are some options:

- Post your question on [Microsoft Q&A](https://learn.microsoft.com/en-us/answers/topics/azure-ad-adal-deprecation.html) and tag it with `[azure-ad-adal-deprecation]`.
- Open an issue in the library's GitHub repository. See the [Languages and frameworks](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview#msal-languages-and-frameworks) section of the MSAL overview article for links to each library's repo.

If you partnered with an Independent Software Vendor \(ISV\) in the development of your application, we recommend that you contact them directly to understand their migration journey to MSAL.

## Next steps

For more information about MSAL, including usage information and which libraries are available for different programming languages and application types, see:

- [Acquire and cache tokens using MSAL](https://learn.microsoft.com/en-us/entra/identity-platform/msal-acquire-cache-tokens)
- [Application configuration options](https://learn.microsoft.com/en-us/entra/identity-platform/msal-client-application-configuration)
- [MSAL authentication libraries](https://learn.microsoft.com/en-us/entra/identity-platform/reference-v2-libraries)
