<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/lifebalance-program-oidc-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure LifeBalance Program for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate LifeBalance Program with Microsoft Entra ID. When you integrate LifeBalance Program with Microsoft Entra ID, you can:

Use Microsoft Entra ID to control who can access LifeBalance Program. Enable your users to be automatically signed in to LifeBalance Program with their Microsoft Entra accounts. Manage your accounts in one central location: the Azure portal.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a Microsoft Entra subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- LifeBalance Program single sign-on \(SSO\) enabled subscription with a custom domain. If you don't have a LifeBalance Program subscription you can visit the [LifeBalance sales page](https://sales.lifebalanceprogram.com/).

## Add LifeBalance Program from the gallery

To configure the integration of LifeBalance Program into Microsoft Entra ID, you need to add LifeBalance Program from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **LifeBalance Program** in the search box.
4. Select **LifeBalance Program** in the results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **LifeBalance Program** > **Single sign-on**.
3. Perform the following steps in the below section:

   1. Select **Go to application**.

      [![Screenshot of showing the identity configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png#lightbox)

   2. Copy **Application \(client\) ID**, **Directory \(tenant\) ID** and use it later in the LifeBalance Program side configuration.

      ![Screenshot shows Settings for the configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/lifebalance-program-oidc-tutorial/directory.png "Settings")

4. Navigate to **Authentication** tab on the left menu and perform the following steps:

   1. In the **Redirect URIs** textbox, use the URL associated with your LifeBalance Program subscription in this format. These usually have the following pattern: `https://<LifeBalance Domain>/api/azure_token`

      - If you do not have a custom domain yet, please contact the [LifeBalance Program support team](mailto:info@lifebalanceprogram.com).


      [![Screenshot of showing the redirect values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/redirect.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/redirect.png#lightbox)

   2. Select **Configure** button.

5. Navigate to **Certificates & secrets** on the left menu and perform the following steps:

   1. Go to **Client secrets** tab and select **+New client secret**.
   2. Enter a valid **Description** in the textbox and select **Expires** days from the drop-down as per your requirement and select **Add**.

      [![Screenshot of showing the client secrets value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png#lightbox)

   3. Once you add a client secret, **Value** is generated. Copy the value and use it later in the LifeBalance Program side configuration.

      [![Screenshot of showing how to add a client secret.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png#lightbox)

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

In this section, you enable B.Simon to use single sign-on by granting access to LifeBalance Program.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **LifeBalance Program**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure LifeBalance Program SSO

To complete the OAuth/OIDC federation setup on **LifeBalance Program** side, you need to send the copied values for Tenant ID, Application ID, and Client Secret from Entra to [LifeBalance Program SSO support team](mailto:sso@lifebalanceprogram.com) via secure email. The LifeBalance SSO team will set these values to have the OIDC connection set properly on both sides.
