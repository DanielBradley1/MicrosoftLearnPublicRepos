<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/spyglass-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Spyglass for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Spyglass with Microsoft Entra ID. When you integrate Spyglass with Microsoft Entra ID, you can:

Use Microsoft Entra ID to control who can access Spyglass. Enable your users to be automatically signed in to Spyglass with their Microsoft Entra accounts. Manage your accounts in one central location: the Azure portal.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Spyglass single sign-on \(SSO\) enabled subscription.

## Add Spyglass from the gallery

To configure the integration of Spyglass into Microsoft Entra ID, you need to add Spyglass from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Spyglass** in the search box.
4. Select **Spyglass** in the results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Spyglass** > **Single sign-on**.
3. Perform the following steps in the below section:

   a. Select **Go to application**.

   ![Screenshot of showing the identity configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png)


   b. Copy **Application \(client\) ID** and **Directory \(tenant\) ID** and use it later in the Spyglass side configuration.


   ![Screenshot of application client values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spyglass-tutorial/application-id.png)


   c. Generate the **Issuer URL** using the following pattern : `https://login.microsoftonline.com/<Tenant_ID>/oauth2`


   Note


   The **Issuer URL** value isn't real. Replace <Tenant\_ID> with actual tenant id value in the Issuer URL pattern.

4. Navigate to **Certificates & secrets** on the left menu and perform the following steps:

   a. Go to **Client secrets** tab and select **+New client secret**. b. Enter a valid **Description** in the textbox and select **Expires** days from the drop-down as per your requirement and select **Add**.

   ![Screenshot of showing the client secrets value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png)


   c. Once you add a client secret, **Value** is generated. Copy the value and use it later in the Spyglass side configuration.


   ![Screenshot of showing how to add a client secret.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png)

Note

In the **Authentication** section, the **Redirect URIs** value is auto populate, you don't need to perform any manual configuration here.

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

In this section, you enable B.Simon to use single sign-on by granting access to Spyglass.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Spyglass**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Spyglass SSO

To configure single sign-on on **Spyglass** side, you need to send the **Client ID, Issuer \(URL\) and Client Secret** values, which you have copied from Entra side to [Spyglass support team](mailto:support@spyglass.software).
