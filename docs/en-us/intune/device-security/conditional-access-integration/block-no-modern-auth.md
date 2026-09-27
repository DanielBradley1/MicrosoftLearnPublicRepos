<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/block-no-modern-auth -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Block Apps That Don't Use Modern Authentication \(MSAL\)

App-based Conditional Access with app protection policies rely on applications using [modern authentication](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), which is an implementation of OAuth2. Most current Office mobile and desktop applications use modern authentication. However, there are third-party apps and older Office apps that use other authentication methods, like basic authentication and forms-based authentication.

## Block access to apps

To block access to apps that don't use modern authentication, use Intune app protection policies to implement Conditional Access. For more information, see [App-based Conditional Access with Intune](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/app-based-policies).

## Additional information

For more information about Microsoft Entra Conditional Access, see the following topics:

- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [How app-based Conditional Access works](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/app-based-policies#how-app-based-conditional-access-works)

## Next steps

- [App-based Conditional Access with Intune](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/app-based-policies)
