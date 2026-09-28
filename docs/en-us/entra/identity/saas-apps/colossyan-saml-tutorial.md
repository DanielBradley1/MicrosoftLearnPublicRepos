<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/colossyan-saml-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Colossyan SAML for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Colossyan SAML with Microsoft Entra ID. When you integrate Colossyan SAML with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Colossyan SAML.
- Enable your users to be automatically signed-in to Colossyan SAML with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Colossyan SAML single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Colossyan SAML supports only **SP** initiated SSO.

## Add Colossyan SAML from the gallery

To configure the integration of Colossyan SAML into Microsoft Entra ID, you need to add Colossyan SAML from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Colossyan SAML** in the search box.
4. Select **Colossyan SAML** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Colossyan SAML

Configure and test Microsoft Entra SSO with Colossyan SAML using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Colossyan SAML.

To configure and test Microsoft Entra SSO with Colossyan SAML, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Colossyan SAML SSO](#configure-colossyan-saml-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Colossyan SAML test user](#create-colossyan-saml-test-user)** - to have a counterpart of B.Simon in Colossyan SAML that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Colossyan SAML** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type the value using the following pattern: `urn:auth0:colossyan:AzureViaSAML`

   b. In the **Reply URL** text box, type the URL: `https://auth.app.colossyan.com/login/callback`

   c. In the **Sign on URL** text box, type the URL: `https://app.colossyan.com/`

   Note

   These Identifier value isn't real. Update the value with the actual Identifier. Contact [Colossyan SAML support team](mailto:info@colossyan.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png "Certificate")

7. On the **Set up Colossyan SAML** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Colossyan SAML SSO

To configure single sign-on on **Colossyan SAML** side, you need to send the downloaded **Certificate \(Raw\)** and appropriate copied URLs from Microsoft Entra admin center to [Colossyan SAML support team](mailto:info@colossyan.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Colossyan SAML test user

In this section, you create a user called B.Simon in Colossyan SAML. Work with [Colossyan SAML support team](mailto:info@colossyan.com) to add the users in the Colossyan SAML platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Colossyan SAML Sign-on URL where you can initiate the login flow.
- Go to Colossyan SAML Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Colossyan SAML tile in the My Apps, this option redirects to Colossyan SAML Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Colossyan SAML you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
