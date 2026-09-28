<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/facebook-federation -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Add Facebook as an identity provider for External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Tip

This article describes adding Facebook as an identity provider for B2B collaboration in workforce tenants. For instructions for external tenants, see [Add Facebook as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-facebook-federation-customers).

You can add Facebook to your self-service sign-up user flows so that users can sign in to your applications using their own Facebook accounts. To allow users to sign in using Facebook, you first need to [enable self-service sign-up](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow) for your tenant. After you add Facebook as an identity provider, set up a user flow for the application and select Facebook as one of the sign-in options.

After you add Facebook as one of your application's sign-in options, on the **Sign in** page a user can enter the email they use for Facebook. Or they can select **Sign-in options** and choose **Sign in with Facebook**. In either case, they're redirected to the Facebook sign-in page for authentication.

![Screenshot of a Microsoft Entra External ID sign-in page showing Sign-in options and the Sign in with Facebook option.](https://learn.microsoft.com/en-us/entra/external-id/media/facebook-federation/sign-in-with-facebook-overview.png)

Note

Users can only use their Facebook accounts to sign up through apps using self-service sign-up and user flows. Users can't be invited and redeem their invitation using a Facebook account.

## Create an app in the Facebook developers console

To use a Facebook account as an [identity provider](https://learn.microsoft.com/en-us/entra/external-id/identity-providers), you need to create an application in the Facebook developers console. If you don't already have a Facebook account, you can sign up at [https://www.facebook.com/](https://www.facebook.com).

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
   3. Enter a URL for the **Terms of Service URL**, for example `https://www.contoso.com/tos`. The Terms of Service URL is a page you maintain to provide terms and conditions for your application.
   4. Enter a URL for the **User Data Deletion**, for example `https://www.contoso.com/delete_my_data`. The User Data Deletion URL is a page you maintain to provide a way for users to request that their data be deleted.
   5. Choose a **Category**, for example **Business and pages**. Facebook requires this value, but it's not used by Microsoft Entra ID.

10. At the bottom of the page, select **Add platform**, select **Website**, and then select **Next**.
11. In **Site URL**, enter the address of your website, for example `https://contoso.com`.
12. Select **Save changes**.
13. Select **Use cases** on the left and select **Customize** next to **Authentication and account creation**.
14. Select **Go to settings** under **Facebook Login**.
15. In **Valid OAuth Redirect URIs**, enter the following URIs, replacing `<tenant-ID>` with your Microsoft Entra tenant ID, `<tenant-subdomain>` with your tenant subdomain, and `<tenant-name>` with your Microsoft Entra tenant name:

- `https://login.microsoftonline.com/te/<tenant-ID>/oauth2/authresp`
- `https://login.microsoftonline.com/te/<tenant-subdomain>.onmicrosoft.com/oauth2/authresp`
- `https://<tenant-name>.ciamlogin.com/<tenant-ID>/federation/oidc/www.facebook.com`
- `https://<tenant-name>.ciamlogin.com/<tenant-name>.onmicrosoft.com/federation/oidc/www.facebook.com`
- `https://<tenant-name>.ciamlogin.com/<tenant-ID>/federation/oauth2`
- `https://<tenant-name>.ciamlogin.com/<tenant-name>.onmicrosoft.com/federation/oauth2`

16. Select **Save changes** and select **Apps** at the top of the page and select the app you've just created.
17. Select **Use cases** on the left hand side of the page and select **Customize** next to **Authentication and account creation**.
18. Add email permissions by selecting **Add** under **Permissions**.
19. Select **Go back** at the top of the page.
20. At this point, only Facebook application owners can sign in. Because you registered the app, you can sign in with your Facebook account. To make your Facebook application available to your users, from the menu, select **Go live**. Follow all of the steps listed to complete all requirements. You'll likely need to complete data handling questions and the business verification to verify your identity as a business entity or organization. For more information, see [Meta App Development](https://developers.facebook.com/docs/development/release).

## Configure a Facebook account as an identity provider

Now you set the Facebook client ID and client secret, either by entering it in the Microsoft Entra admin center or by using PowerShell. You can test your Facebook configuration by signing up via a user flow on an app enabled for self-service sign-up.

### To configure Facebook federation in the Microsoft Entra admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [External Identity Provider Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#external-identity-provider-administrator).
2. Browse to **Entra ID** > **External Identities** > **All identity providers**, then on the **Facebook** line, select **Configure**.
3. For the **Client ID**, enter the **App ID** of the Facebook application that you created earlier.
4. For the **Client secret**, enter the **App secret** that you recorded.

   ![Screenshot of the Facebook identity provider configuration pane in the Microsoft Entra admin center with Client ID and Client secret fields.](https://learn.microsoft.com/en-us/entra/external-id/media/facebook-federation/add-social-identity-provider-page.png)
5. Select **Save**.

### To configure Facebook federation by using PowerShell

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


   You might need to [enable self-service sign-up for your tenant](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow#enable-self-service-sign-up-for-your-tenant).


   Note


   Use the client ID and client secret from the app you created in the Facebook developer console. For more information, see the [New-MgIdentityProvider](https://learn.microsoft.com/en-us/powershell/microsoftgraph/authentication-commands) article.

## How do I remove Facebook federation?

You can delete your Facebook federation setup. If you do so, any users who have signed up through user flows with their Facebook accounts will no longer be able to sign in.

### To delete Facebook federation in the Microsoft Entra admin center:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [External Identity Provider Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#external-identity-provider-administrator).
2. Browse to **Entra ID** > **External Identities** > **All identity providers**.
3. Select the **Facebook** line. Select **Configured**, and then select **Delete**.
4. Select **Yes** to confirm deletion.

### To delete Facebook federation by using PowerShell:

1. Install the latest version of the [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation).
2. Run the following command:

   ```powershell
   Connect-MgGraph -Scopes "IdentityProvider.ReadWrite.All"
   ```

3. In the sign-in prompt, sign in as at least an [External Identity Provider Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#external-identity-provider-administrator).
4. Enter the following command:

   ```powershell
   Remove-MgIdentityProvider -IdentityProviderBaseId "Facebook-OAUTH"
   ```


   Note


   For more information, see [Remove-MgIdentityProvider](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.signins/remove-mgidentityprovider).

## Related content

- [SAML/WS-Fed IdP federation](https://learn.microsoft.com/en-us/entra/external-id/direct-federation)
- [Google federation](https://learn.microsoft.com/en-us/entra/external-id/google-federation)
