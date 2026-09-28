<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/websphere-liberty-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure WebSphere Liberty for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate WebSphere Liberty with Microsoft Entra ID. When you integrate WebSphere Liberty with Microsoft Entra ID, you can:

- Use Microsoft Entra ID to control who can access WebSphere Liberty.
- Enable your users to be automatically signed in to WebSphere Liberty with their Microsoft Entra accounts.
- Manage your accounts in one central location: the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- WebSphere Liberty single sign-on \(SSO\) enabled subscription.

## Add WebSphere Liberty from the gallery

To configure the integration of WebSphere Liberty into Microsoft Entra ID, you need to add WebSphere Liberty from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **WebSphere Liberty** in the search box.
4. Select **WebSphere Liberty** in the results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **WebSphere Liberty** > **Single sign-on**.
3. Perform the following steps in the below section:

   1. Select **Go to application**.

      ![Screenshot of showing the identity configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png)

   2. Copy **Application \(client\) ID** and use it later in the WebSphere Liberty side configuration.

      ![Screenshot of application client values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-id.png)

   3. Under **Endpoints** tab, copy **OpenID Connect metadata document** link and use it later in the WebSphere Liberty side configuration.

      ![Screenshot of showing the endpoints on tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/endpoints.png)

4. Navigate to **Authentication** tab on the left menu and perform the following steps:

   1. In the **Redirect URIs** textbox, type a URL using the following pattern: `https://<HOST_NAME>:<SSL_PORT>/oidcclient/redirect/<ClientID>`

      ![Screenshot of showing the redirect values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/redirect.png)

   2. Select **Configure** button.

5. Navigate to **Certificates & secrets** on the left menu and perform the following steps:

   1. Go to **Client secrets** tab and select **+New client secret**.
   2. Enter a valid **Description** in the textbox and select **Expires** days from the drop-down as per your requirement and select **Add**.

      ![Screenshot of showing the client secrets value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png)

   3. Once you add a client secret, **Value** is generated. Copy the value and use it later in the WebSphere Liberty side configuration.

      ![Screenshot of showing how to add a client secret.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure WebSphere Liberty SSO

To complete the OAuth/OIDC federation setup on **WebSphere Liberty** side, you need to send the copied values like Tenant ID, Application ID, and Client Secret from Entra to [WebSphere Liberty support team](mailto:support@ibm.com). They set this setting to have the OIDC connection set properly on both sides.
