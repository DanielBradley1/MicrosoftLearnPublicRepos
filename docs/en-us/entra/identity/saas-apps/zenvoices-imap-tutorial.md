<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zenvoices-imap-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Zenvoices IMAP for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Zenvoices IMAP with Microsoft Entra ID. When you integrate Zenvoices IMAP with Microsoft Entra ID, you can:

Use Microsoft Entra ID to control who can access Zenvoices IMAP. Enable your users to be automatically signed in to Zenvoices IMAP with their Microsoft Entra accounts. Manage your accounts in one central location: the Azure portal.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Zenvoices IMAP single sign-on \(SSO\) enabled subscription.

## Add Zenvoices IMAP from the gallery

To configure the integration of Zenvoices IMAP into Microsoft Entra ID, you need to add Zenvoices IMAP from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Zenvoices IMAP** in the search box.
4. Select **Zenvoices IMAP** in the results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Zenvoices IMAP** > **Single sign-on**.
3. Perform the following steps in the following section:

   1. Select **Go to application**.

      ![Screenshot of showing the identity configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png)

   2. Copy **Application \(client\) ID** and use it later in the Zenvoices IMAP side configuration.

      ![Screenshot of application client values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-id.png)

   3. Under **Endpoints** tab, copy **OpenID Connect metadata document** link and use it later in the Zenvoices IMAP side configuration.

      ![Screenshot of showing the endpoints on tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/endpoints.png)

4. Navigate to **Authentication** tab on the left menu and perform the following steps:

   1. In the **Redirect URIs** textbox, type the URL: `https://app.zenvoices.com/ChannelConnector/ProcessEntraIMAPAuthorizationResult`

      ![Screenshot of showing the redirect values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/redirect.png)

   2. Select **Configure** button.

5. Navigate to **Certificates & secrets** on the left menu and perform the following steps:

   1. Go to **Client secrets** tab and select **+New client secret**.
   2. Enter a valid **Description** in the textbox and select **Expires** days from the drop-down as per your requirement and select **Add**.

      ![Screenshot of showing the client secrets value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png)

   3. Once you add a client secret, **Value** is generated. Copy the value and use it later in the Zenvoices IMAP side configuration.

      ![Screenshot of showing how to add a client secret.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png)

### Create a Microsoft Entra test user

In this section, you create a test user called B.Simon.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. Select **New user** > **Create new user**, at the top of the screen.
4. In the **User** properties, follow these steps:

   1. In the **Display name** field, enter `B.Simon`.
   2. In the **User principal name** field, enter the username@companydomain.extension. For example, `B.Simon@contoso.com`.
   3. Select the **Show password** check box, and then write down the value that's displayed in the **Password** box.
   4. Select **Review + create**.

5. Select **Create**.

### Assign the Microsoft Entra test user

In this section, you enable B.Simon to use single sign-on by granting access to Zenvoices IMAP.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Zenvoices IMAP**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Zenvoices IMAP SSO

To complete the OAuth/OIDC federation setup on **Zenvoices IMAP** side, you need to send the copied values like Tenant ID, Application ID, and Client Secret from Entra to [Zenvoices IMAP support team](mailto:info@zenvoices.com). They set this setting to have the OIDC connection set properly on both sides.
