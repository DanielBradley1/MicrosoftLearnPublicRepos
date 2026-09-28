<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/raketa-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Raketa for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Raketa with Microsoft Entra ID. When you integrate Raketa with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Raketa.
- Enable your users to be automatically signed-in to Raketa with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Raketa single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Raketa supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Raketa from the gallery

To configure the integration of Raketa into Microsoft Entra ID, you need to add Raketa from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Browse Microsoft Entra Gallery** page, in the search box, type *Raketa* in the search box.
4. Select **Raketa**. In the **Raketa** pane, provide a name and select **Create**.

## Configure and test Microsoft Entra SSO for Raketa

Configure and test Microsoft Entra SSO with Raketa using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Raketa.

To configure and test Microsoft Entra SSO with Raketa, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Raketa SSO](#configure-raketa-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Raketa test user](#create-raketa-test-user)** - to have a counterpart of B.Simon in Raketa that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Raketa** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.

   ![rkt\_5](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/raketa-tutorial/method.png)

4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.
5. On the **Basic SAML Configuration** section, perform the following steps:

   1. In the **Identifier \(Entity ID\)** and **Sign on URL** text boxes, type the URL: `https://raketa.travel/`.
   2. In the **Reply URL** text box, type a URL using the following pattern: `https://raketa.travel/sso/acs?clientId=<CLIENT_ID>`.


   ![rkt\_6](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/raketa-tutorial/values.png)


   Note


   The Reply URL value isn't real. Update the value with the actual Reply URL. Contact [Raketa Client support team](mailto:help@raketa.travel) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.
7. On the **Set up Raketa** section, copy the appropriate URL\(s\) based on your requirement.

   1. **Login URL** – The authorization web-page URL, which is used to redirect the users to the authentication system.
   2. **Microsoft Entra Identifier** – Microsoft Entra Identifier.
   3. **Logout URL** – The web-page URL, which is used to redirect the users after logout.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Raketa SSO

To configure single sign-on on **Raketa** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Raketa support team](mailto:help@raketa.travel). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Raketa test user

In this section, you create a user called B.Simon in Raketa. Work with [Raketa support team](mailto:help@raketa.travel) to add the users in the Raketa platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Raketa Sign-on URL where you can initiate the login flow.
- Go to Raketa Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Raketa tile in the My Apps, this option redirects to Raketa Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Raketa you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
