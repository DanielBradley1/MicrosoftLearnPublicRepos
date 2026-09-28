<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/glia-hub-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Glia Hub for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Glia Hub with Microsoft Entra ID. When you integrate Glia Hub with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Glia Hub.
- Enable your users to be automatically signed-in to Glia Hub with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Glia Hub single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Glia Hub supports **SP and IDP** initiated SSO.

## Adding Glia Hub from the gallery

To configure the integration of Glia Hub into Microsoft Entra ID, you need to add Glia Hub from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Glia Hub** in the search box.
4. Select **Glia Hub** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Glia Hub

Configure and test Microsoft Entra SSO with Glia Hub using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Glia Hub.

To configure and test Microsoft Entra SSO with Glia Hub, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Glia Hub SSO](#configure-glia-hub-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Glia Hub test user](#create-glia-hub-test-user)** - to have a counterpart of B.Simon in Glia Hub that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Glia Hub** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   1. In the **Identifier** textbox, type a URL using the following pattern: `https://<CustomerName>.app.glia.com`
   2. In the **Reply URL** textbox, type a URL using the following pattern: `https://<CustomerName>.app.glia.com/saml/acs`
   3. In the **Relay State** textbox, type a URL using the following pattern: `https://<CustomerName>.app.glia.com`
   4. In the **Logout Url** textbox, type a URL using the following pattern: `https://<CustomerName>.app.glia.com/saml/logout`

6. Perform the following step, if you wish to configure the application in **SP** initiated mode:

   1. In the **Sign on URL** textbox, type a URL using the following pattern: `https://<CustomerName>.app.glia.com`


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL, Sign on URL, Relay State and Logout Url. Contact [Glia Hub support team](mailto:support@glia.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

7. Glia Hub application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

8. In addition to above, Glia Hub application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | idp\_name\_attribute | user.userprincipalname |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Glia Hub SSO

To configure single sign-on on **Glia Hub** side, you need to send the **App Federation Metadata Url** to [Glia Hub support team](mailto:support@glia.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Glia Hub test user

In this section, you create a user called B.Simon in Glia Hub. Work with [Glia Hub support team](mailto:support@glia.com) to add the users in the Glia Hub platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Glia Hub Sign on URL where you can initiate the login flow.
- Go to Glia Hub Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application** in Microsoft Entra admin center and you should be automatically signed in to the Glia Hub for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Glia Hub tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Glia Hub for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Glia Hub you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
