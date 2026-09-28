<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/simple-sign-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Simple Sign for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Simple Sign with Microsoft Entra ID. When you integrate Simple Sign with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Simple Sign.
- Enable your users to be automatically signed-in to Simple Sign with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Simple Sign single sign-on enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Simple Sign supports **IDP** initiated SSO.

## Add Simple Sign from the gallery

To configure the integration of Simple Sign into Microsoft Entra ID, you need to add Simple Sign from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Simple Sign** in the search box.
4. Select **Simple Sign** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Simple Sign

Configure and test Microsoft Entra SSO with Simple Sign using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Simple Sign.

To configure and test Microsoft Entra SSO with Simple Sign, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Simple Sign SSO](#configure-simple-sign-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Simple Sign test user](#create-simple-sign-test-user)** - to have a counterpart of B.Simon in Simple Sign that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Simple Sign** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Set up Single Sign-On with SAML** page, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.simplesign.io/saml/simplesamlphp/www/module.php/saml/sp/metadata.php/cloudfish-sp`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.simplesign.io/saml/simplesamlphp/www/module.php/saml/sp/saml2-acs.php/cloudfish-sp`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Simple Sign Client support team](mailto:info@simplesign.io) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Simple Sign** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Simple Sign SSO

To configure single sign-on on **Simple Sign** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Simple Sign support team](mailto:info@simplesign.io). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Simple Sign test user

In this section, you create a user called Britta Simon in Simple Sign. Work with [Simple Sign support team](mailto:info@simplesign.io) to add the users in the Simple Sign platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Simple Sign for which you set up the SSO.
- You can use Microsoft My Apps. When you select the Simple Sign tile in the My Apps, you should be automatically signed in to the Simple Sign for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Simple Sign you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
