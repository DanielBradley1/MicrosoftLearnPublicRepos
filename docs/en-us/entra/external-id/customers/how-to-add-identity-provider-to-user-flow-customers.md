<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-add-identity-provider-to-user-flow-customers -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Add an identity provider to a user flow

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

After you configure an external identity provider in your external tenant, you need to add it to a user flow to make it available on the sign-in page.

For steps on configuring identity providers, see:

- [Configure a custom OIDC identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers)
- [Add a Microsoft Entra ID tenant as an OIDC identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-entra-id-federation-customers)
- [Configure SAML/WS-Fed IdP federation](https://learn.microsoft.com/en-us/entra/external-id/direct-federation)
- [Add Google as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-google-federation-customers)
- [Add Facebook as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-facebook-federation-customers)
- [Add Apple as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers)
- [Add Microsoft account as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-microsoft-accounts-federation-customers)

## Prerequisites

- An [external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).
- A registered application in the tenant.
- A configured identity provider \(see links above\).
- A [sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).

## Add the identity provider to a user flow

To add a configured identity provider to a user flow, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [External ID User Flow Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#external-id-user-flow-administrator).
2. Switch to your external tenant by selecting the **Settings** icon in the top menu and choosing the external tenant.
3. Browse to **Entra ID** > **External Identities** > **User flows**.
4. Select the user flow where you want to add the identity provider.

   ![Screenshot of the External Identities User flows page showing the user flow list.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-identity-provider-to-user-flow-customers/select-user-flow.png)
5. Under **Settings**, select **Identity providers**.
6. Under **Other Identity Providers**, select the identity provider you want to add.

   ![Screenshot of the Identity providers page showing the Other Identity Providers section.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-identity-provider-to-user-flow-customers/select-identity-provider.png)
7. Select **Save**.

## Next step

[Test your sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-test-user-flows)
