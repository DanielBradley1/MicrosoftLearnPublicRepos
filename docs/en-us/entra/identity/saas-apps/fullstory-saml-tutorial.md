<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/fullstory-saml-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# Configure Fullstory SAML for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Fullstory SAML with Microsoft Entra ID. When you integrate Fullstory SAML with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Fullstory SAML.
- Enable your users to be automatically signed-in to Fullstory SAML with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Fullstory SAML single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Fullstory SAML supports only **SP** initiated SSO.
- Fullstory SAML supports **Just In Time** user provisioning.

## Add Fullstory SAML from the gallery

To configure the integration of Fullstory SAML into Microsoft Entra ID, you need to add Fullstory SAML from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Fullstory SAML** in the search box.
4. Select **Fullstory SAML** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Fullstory SAML

Configure and test Microsoft Entra SSO with Fullstory SAML using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Fullstory SAML.

To configure and test Microsoft Entra SSO with Fullstory SAML, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Fullstory SAML SSO](#configure-fullstory-saml-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Fullstory SAML test user](#create-fullstory-saml-test-user)** - to have a counterpart of B.Simon in Fullstory SAML that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Fullstory SAML** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a value using the following pattern: `urn:auth0:fullstory:<Entity ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://fullstory.auth0.com/login/callback?connection=<Entity ID>`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://app.fullstory.com/sso/<Entity ID>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Fullstory SAML support team](mailto:support@fullstory.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federated Certificate \(XML\)** and select **Download** to download the IdP-generated metadata.xml file and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificate-base64-download.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Fullstory SAML SSO

To configure single sign-on on **Fullstory SAML** side, you need to the download the **Federated Certificate \(XML\)** to copy and paste the contents of your IdP-generated metadata.xml file into Fullstory to complete the configuration. For more information, please refer [this](https://help.fullstory.com/hc/articles/360020623014-How-do-I-configure-SSO) document.

### Create Fullstory SAML test user

In this section, a user called Britta Simon is created in Fullstory SAML. Fullstory SAML supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Fullstory SAML, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Fullstory SAML Sign-on URL where you can initiate the login flow.
- Go to Fullstory SAML Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Fullstory SAML tile in the My Apps, this option redirects to Fullstory SAML Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Fullstory SAML you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
