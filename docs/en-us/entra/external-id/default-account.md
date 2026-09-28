<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/default-account -->
<!-- Sitemap-Last-Modified: 2026-03-27 -->

# Use Microsoft Entra work and school accounts for B2B collaboration

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Microsoft Entra ID is available as an identity provider option for B2B collaboration by default. If an external guest user has a Microsoft Entra account through work or school, they can redeem your B2B collaboration invitations or complete your sign-up user flows using their Microsoft Entra account.

## Guest sign-in using Microsoft Entra accounts

If you want to enable guest users to sign in with their Microsoft Entra account, you can use either the invitation flow or a self-service sign-up user flow. No further configuration is required.

### Microsoft Entra account in the invitation flow

When you [invite a guest user](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator) to B2B collaboration, you can specify their Microsoft Entra account as the **Email address** they use to sign in.

[![Screenshot of inviting a guest user using the Microsoft Entra account.](https://learn.microsoft.com/en-us/entra/external-id/media/default-account/default-account-invite.png)](https://learn.microsoft.com/en-us/entra/external-id/media/default-account/default-account-invite.png#lightbox)

### Microsoft Entra account in self-service sign-up user flows

Microsoft Entra account is an identity provider option for your self-service sign-up user flows. Users can sign up for your applications using their own Microsoft Entra accounts. First, [enable self-service sign-up](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow) for your tenant, and then set up a user flow for the application.

[![Screenshot of Microsoft Entra account in a self-service sign-up user flow.](https://learn.microsoft.com/en-us/entra/external-id/media/default-account/default-account-user-flow.png)](https://learn.microsoft.com/en-us/entra/external-id/media/default-account/default-account-user-flow.png#lightbox)

## Verifying the application's publisher domain

As of November 2020, new application registrations show up as unverified in the user consent prompt unless [the application's publisher domain is verified](https://learn.microsoft.com/en-us/entra/identity-platform/howto-configure-publisher-domain), ***and*** the company’s identity has been verified with the Microsoft Partner Network and associated with the application. \([Learn more](https://learn.microsoft.com/en-us/entra/identity-platform/publisher-verification-overview) about this change.\) For Microsoft Entra user flows, the publisher’s domain appears only when using a [Microsoft account](https://learn.microsoft.com/en-us/entra/external-id/microsoft-account) or other Microsoft Entra tenant as the identity provider. To meet these new requirements, follow these steps:

1. [Verify your company identity using your Microsoft Partner Network \(MPN\) account](https://learn.microsoft.com/en-us/partner-center/verification-responses). This process verifies information about your company and your company’s primary contact.
2. Complete the publisher verification process to associate your MPN account with your app registration using one of the following options:

   - If the app registration for the Microsoft account identity provider is in a Microsoft Entra tenant, [verify your app in the App Registration portal](https://learn.microsoft.com/en-us/entra/identity-platform/mark-app-as-publisher-verified).
   - If your app registration for the Microsoft account identity provider is in an Azure AD B2C tenant, [mark your app as publisher verified using Microsoft Graph APIs](https://learn.microsoft.com/en-us/entra/identity-platform/troubleshoot-publisher-verification#making-microsoft-graph-api-calls) \(for example, using Graph Explorer\).

## Next steps

- [Microsoft account](https://learn.microsoft.com/en-us/entra/external-id/microsoft-account)
- [Add Microsoft Entra B2B collaboration users](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator)
- [Add self-service sign-up to an app](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow)
