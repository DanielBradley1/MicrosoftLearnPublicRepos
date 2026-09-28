<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-facebook-federation-customers -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Add Facebook as an identity provider

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

By setting up federation with Facebook, you can allow customers to sign in to your applications with their own Facebook accounts. \(Learn more about [authentication methods and identity providers for customers](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-authentication-methods-customers).\)

## Create a Facebook application

To enable sign-in for customers with a Facebook account, you need to create an application in [Facebook App Dashboard](https://developers.facebook.com/). For more information, see [App Development](https://developers.facebook.com/docs/development).

If you don't already have a Facebook account, sign up at [https://www.facebook.com](https://www.facebook.com). After you sign-up or sign-in with your Facebook account, start the [Facebook developer account registration process](https://developers.facebook.com/async/registration). For more information, see [Register as a Facebook Developer](https://developers.facebook.com/docs/development/register).

Note

This document was created using the state of the provider’s developer page at the time of creation, and changes may occur.

1. Sign in to [Facebook for developers](https://developers.facebook.com/apps) with your Facebook developer account credentials.
2. If you haven't already done so, register as a Facebook developer: Select **Get Started** in the upper-right corner of the page, accept Facebook's policies, and complete the registration steps.
3. Select **Create App**. This step may require you to accept Facebook platform policies and complete an online security check.
4. Select **Authenticate and request data from users with Facebook Login** > **Next**.
5. Under **Are you building a game?** select **No, I'm not building a game** and then **Next**.
6. Add an app name and a valid app contact email. You can also add a business account if you have one.
7. Select **Create app**.
8. Once your app is created, go to the Dashboard.
9. Select **App settings** > **Basic**.

   1. Copy the value of **App ID**. Then select **Show** and copy the value of **App Secret**. You use both of these values to configure Facebook as an identity provider in your tenant. **App Secret** is an important security credential.
   2. Enter a URL for the **Privacy Policy URL**, for example `https://www.contoso.com/privacy`. The policy URL is a page you maintain to provide privacy information for your application.
   3. Enter a URL for the **Terms of Service URL**, for example `https://www.contoso.com/tos`. The policy URL is a page you maintain to provide terms and conditions for your application.
   4. Enter a URL for the **User Data Deletion**, for example `https://www.contoso.com/delete_my_data`. The User Data Deletion URL is a page you maintain to provide away for users to request that their data be deleted.
   5. Choose a **Category**, for example **Business and pages**. Facebook requires this value, but it's not used by Microsoft Entra ID.

10. At the bottom of the page, select **Add platform**, select **Website**, and then select **Next**.
11. In **Site URL**, enter the address of your website, for example `https://contoso.com`.
12. Select **Save changes**.
13. Select **Use cases** on the left and select **Customize** next to **Authentication and account creation**.
14. Select **Go to settings** under **Facebook Login**.
15. In **Valid OAuth Redirect URIs**, enter the following URIs, replacing `<tenant-ID>` with your **external tenant ID** and `<tenant-name>` with your **external tenant name**:

- `https://login.microsoftonline.com/te/<tenant-ID>/oauth2/authresp`
- `https://login.microsoftonline.com/te/<tenant-name>.onmicrosoft.com/oauth2/authresp`
- `https://<tenant-name>.ciamlogin.com/<tenant-ID>/federation/oidc/www.facebook.com`
- `https://<tenant-name>.ciamlogin.com/<tenant-name>.onmicrosoft.com/federation/oidc/www.facebook.com`
- `https://<tenant-name>.ciamlogin.com/<tenant-ID>/federation/oauth2`
- `https://<tenant-name>.ciamlogin.com/<tenant-name>.onmicrosoft.com/federation/oauth2`

16. Select **Save changes** and select **Apps** at the top of the page and select the app you've just created.
17. Select **Use cases** on the left hand side of the page and select **Customize** next to **Authentication and account creation**.
18. Add email permissions by selecting **Add** under **Permissions**.
19. Select **Go back** at the top of the page.
20. At this point, only Facebook application owners can sign in. Because you registered the app, you can sign in with your Facebook account. To make your Facebook application available to your users, from the menu, select **Go live**. Follow all of the steps listed to complete all requirements. You'll likely need to complete data handling questions and the business verification to verify your identity as a business entity or organization. For more information, see [Meta App Development](https://developers.facebook.com/docs/development/release).

## Configure Facebook federation in Microsoft Entra External ID

After you create the Facebook application, in this step you set the Facebook client ID and client secret in Microsoft Entra ID. You can use the Microsoft Entra admin center or PowerShell to do so. To configure Facebook federation in the Microsoft Entra admin center, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **All identity providers**.
3. On the **Built-in** tab, next to **Facebook**, select **Configure**.
4. Enter a **Name**. For example, *Facebook*.
5. For the **Client ID**, enter the App ID of the Facebook application that you created earlier.
6. For the **Client secret**, enter the App Secret that you recorded.
7. Select **Save**.

To configure Facebook federation by using PowerShell, follow these steps:

1. Install the latest version of the [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation).
2. Run the following command:

   ```powershell
   Connect-MgGraph -Scopes "IdentityProvider.ReadWrite.All"
   ```

3. At the sign-in prompt, sign in as at least an [External Identity Provider Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#external-identity-provider-administrator).
4. Run the following commands:

   ```powershell
   $params = @{
      "@odata.type" = "microsoft.graph.socialIdentityProvider"
      displayName = "Facebook"
      identityProviderType = "Facebook"
      clientId = "[Client ID]"
      clientSecret = "[Client secret]"
   }

   New-MgIdentityProvider -BodyParameter $params
   ```

Use the client ID and client secret from the app you created in [Create a Facebook application](#create-a-facebook-application) step.

## Enable users to sign in and sign up with the identity provider

After you configure Facebook as an identity provider, add it to a user flow to allow sign-in and sign-up with the identity provider. See [Add an identity provider to a user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-add-identity-provider-to-user-flow-customers).

## Related content

- [Add Apple as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers)
- [Add a Microsoft Entra ID tenant as an OIDC identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-entra-id-federation-customers)
- [Add OpenID Connect as an external identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers)
