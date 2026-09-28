<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-microsoft-accounts-federation-customers -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Add Microsoft account \(live.com\) as an OpenID Connect identity provider

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Setting up federation with Microsoft account \(live.com\) by using an OpenID Connect \(OIDC\) identity provider and adding it to your user flow enables users to sign up and sign in to your applications by using their existing Microsoft accounts \(MSA\).

## Prerequisites

- An [external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).
- A [sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).
- A Microsoft account \(live.com\). If you don't already have one, sign up at [https://www.live.com/](https://www.live.com/).

Note

This feature is available only for users who sign up with a Microsoft account \(MSA\). It isn’t available for [B2B guest users](https://learn.microsoft.com/en-us/entra/external-id/user-properties) invited to the tenant.

## Create a Microsoft account application

To enable sign-in for users with a Microsoft account, you need to create an application in a Microsoft Entra ID tenant. The resource tenant for the application can be any Microsoft Entra ID tenant, like your workforce or external tenant.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **App registrations** then select **New registration**.
3. Name the application, for example *ContosoApp*.
4. Under **Supported account types**, select *Accounts in any organizational directory \(Any Microsoft Entra ID tenant - Multitenant\) and personal Microsoft accounts \(for example, Skype, Xbox\)*.
5. Under **Redirect URI**, select **Web** and enter your populated redirect URI described in [Set up your OpenID Connect identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers#set-up-your-openid-connect-identity-provider).
6. Select **Register**.

   When registration finishes, the Microsoft Entra admin center displays the app registration's **Overview** pane. You see the **Application \(client\) ID**. Record this value, as you need it later.
7. Under **Manage**, browse to **Certificates & secrets**, and then select **New client secret**.
8. Name the secret, for example *Key 1*, and then select **Add**.
9. Record the **Value** of the secret, as you need it later. Make sure you save the secret before leaving the page. Client secret values can't be viewed except immediately after creation.

### Configure optional claims

You can also configure optional claims to be provided for your application such as *family\_name* and *given\_name*.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **App registrations**.
3. Select your MSA application that you created earlier.
4. Under **Manage**, select **Token configuration**.
5. Select **Add optional claim**.
6. Select the token type you want to configure, such as *ID*.
7. Select the optional claims to add.
8. Select **Add**.

## Configure Microsoft account \(live.com\) as an OpenID Connect identity provider

Once you have configured your Microsoft account \(live.com\) as an application, you can proceed to set it up as an OIDC identity provider in your external tenant.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [External Identity Provider Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#external-identity-provider-administrator).
2. Browse to **Entra ID** > **External identities** > **All identity providers**.
3. Select the **Custom** tab, and then select **Add new** > **Open ID Connect**.

   ![Screenshot of the All identity providers page showing the Custom tab and the Add new menu with Open ID Connect selected.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-custom-oidc-federation-customers/add-new.jpg)
4. Enter the following details for your identity provider on the **Basics** tab:

   - **Display name**: Enter a name for your identity provider, for example *Microsoft account* This name is displayed to your users during the sign-in and sign-up flows. For example, *Sign in with Microsoft account* or *Sign up with your Microsoft account*.
   - **Well-known endpoint**: Enter the endpoint URI as `https://login.microsoftonline.com/consumers/v2.0/.well-known/openid-configuration`, which is the discovery URI of the common authority URL for Microsoft accounts.
   - **OpenID Issuer URI**: Enter the Issuer URI as `https://login.live.com`.
   - **Client ID** and **Client Secret**: Enter the **Application \(client\) ID** and **Value** of the client secret you created earlier.
   - **Client Authentication**: Select **client\_secret** and add `openid profile email` to **Scope**.
   - **Response type**: Select **code**.

5. You can select **Next: Claims mapping** to configure [claims mapping](https://learn.microsoft.com/en-us/entra/external-id/customers/reference-oidc-claims-mapping-customers) or **Review + create** to add your identity provider.

   ![Screenshot of the Basics tab for an Open ID Connect identity provider configured for Microsoft account, including endpoint, issuer, client ID, secret, and scope values.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-microsoft-accounts-federation-customers/msa-setup.png)

## Enable users to sign in and sign up with the identity provider

After you configure Microsoft account as an identity provider, add it to a user flow to allow sign-in and sign-up with the identity provider. See [Add an identity provider to a user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-add-identity-provider-to-user-flow-customers).

## Related content

- [Add an Azure AD B2C tenant as an OIDC identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-b2c-federation-customers)
- [OIDC claims mapping](https://learn.microsoft.com/en-us/entra/external-id/customers/reference-oidc-claims-mapping-customers)
