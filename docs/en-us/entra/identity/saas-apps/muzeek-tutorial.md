<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/muzeek-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Muzeek for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Muzeek with Microsoft Entra ID. When you integrate Muzeek with Microsoft Entra ID, you can:

Use Microsoft Entra ID to control who can access Muzeek. Enable your users to be automatically signed in to Muzeek with their Microsoft Entra accounts. Manage your accounts in one central location: the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Muzeek single sign-on \(SSO\) enabled subscription.

## Add Muzeek from the gallery

To configure the integration of Muzeek into Microsoft Entra ID, you need to add Muzeek from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Muzeek** in the search box.
4. Select **Muzeek** in the results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Muzeek** > **Single sign-on**.
3. Perform the following steps in the below section:

   a. Select **Go to application**.

   [![Screenshot showing the identity configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/go-to-application.png#lightbox)


   b. Copy **Application \(client\) ID** and **Directory \(tenant\) ID**, use it later in the Muzeek side configuration.


   ![Screenshot of application client values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/application-id.png)

4. Navigate to **Authentication** tab on the left menu and perform the following steps:

   a. Enable the **Access tokens** and **ID tokens**

   [![Screenshot showing the Access tokens.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/access-token.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/access-token.png#lightbox)


   b. select **Save**.


   Note


   The **Redirect URIs** value is auto populate, you don't need to perform any manual configuration here.

5. Navigate to **Certificates & secrets** on the left menu and perform the following steps:

   1. Go to **Client secrets** tab and select **+New client secret**.
   2. Enter a valid **Description** in the textbox and select **Expires** days from the drop-down as per your requirement and select **Add**.

      [![Screenshot showing the client secrets value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client-secret.png#lightbox)

   3. Once you add a client secret, **Value** is generated. Copy the value and use it later in the Muzeek side configuration.

      [![Screenshot showing how to add a client secret.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/client.png#lightbox)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Muzeek SSO

Below are the configuration steps to complete the OIDC federation setup:

1. Sign into the Muzeek site as an administrator.
2. Select **Settings** icon at the bottom of the page and perform of the below steps.

   [![Screenshot showing Muzeek configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/configuration.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/configuration.png#lightbox)


   a. Go to the **Integrations** tab.


   b. In the **ENTRA Domain** field, enter the domain URL value using the following pattern: `https://login.microsoftonline.com/<Tenant_ID>/oauth2/v2.0/authorize`


   Note


   The domain URL value isn't real, replace the **Tenant\_ID** value with actual **Directory \(tenant\) ID**, which you have copied from Entra side.


   c. In the **ENTRA Client ID** field, paste the **Application ID** value, which you have copied from Entra page.


   d. In the **ENTRA Client Secret** field, paste the value, which you have copied from **Certificates & secrets** section at Entra side.


   e. Select **Save Changes**.


   f. Once saved, Muzeek populates the **Home Page URL** which can be used later in [Connect SSO via MyApps](#connect-sso-via-myapps) section. [![Screenshot showing the details of Home Page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/image.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/image.png#lightbox)

## Connect SSO via MyApps

To connect your MyApps account to Muzeek in the Microsoft Entra admin center, please follow the below steps:

1. Navigate to **App Registrations** > \*\*Muzeek **Branding & Properties**. [![Screenshot showing the app registrations of Muzeek.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/home.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/muzeek-tutorial/home.png#lightbox)
2. Paste the Home Page URL you copied from Muzeek portal into the **Home Page URL** field in Microsoft Entra admin center.
3. Select **Save** and wait for 10 - 15 minutes for the change to propagate in the system.

Once done, you should now be able to successfully navigate to your Muzeek account while logged into MyApps, and any users you have added to your tenant should be able to do so as well.
