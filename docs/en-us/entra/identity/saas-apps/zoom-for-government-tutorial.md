<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zoom-for-government-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# Configure Zoom for Government for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Zoom for Government with Microsoft Entra ID. When you integrate Zoom for Government with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Zoom for Government.
- Enable your users to be automatically signed-in to Zoom for Government with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Zoom for Government single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Zoom for Government supports only **SP** initiated SSO.
- Zoom for Government supports **Just In Time** user provisioning.

## Add Zoom for Government from the gallery

To configure the integration of Zoom for Government into Microsoft Entra ID, you need to add Zoom for Government from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Zoom for Government** in the search box.
4. Select **Zoom for Government** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Zoom for Government

Configure and test Microsoft Entra SSO with Zoom for Government using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Zoom for Government.

To configure and test Microsoft Entra SSO with Zoom for Government, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Zoom for Government SSO](#configure-zoom-for-government-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Zoom for Government test user](#create-zoom-for-government-test-user)** - to have a counterpart of B.Simon in Zoom for Government that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Zoom for Government** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<CustomerName>.zoomgov.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<CustomerName>.zoomgov.com`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://<CustomerName>.zoomgov.com`

   d. In the **Logout URL** text box, type a URL using the following pattern: `https://<CustomerName>.zoomgov.com`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL, Sign on URL and Logout URL. Contact [Zoom for Government support team](mailto:support@zoomgov.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. Zoom for Government application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

7. In addition to above, Zoom for Government application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | mail | user.mail |
   | phone | user.telephonenumber |
   | department | user.department |
   | role | user.assignedroles |
   | groups | user.groups |


   Note


   Please select [here](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-roles-ui) to know how to configure Role in Microsoft Entra ID.

8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png "Certificate")

9. On the **Set up Zoom for Government** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Zoom for Government SSO

To configure single sign-on on **Zoom for Government** side, you need to send the downloaded **Certificate \(Raw\)** and appropriate copied URLs from Microsoft Entra admin center to [Zoom for Government support team](mailto:support@zoomgov.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Zoom for Government test user

In this section, a user called Britta Simon is created in Zoom for Government. Zoom for Government supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Zoom for Government, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Zoom for Government Sign-on URL where you can initiate the login flow.
- Go to Zoom for Government Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Zoom for Government tile in the My Apps, this option redirects to Zoom for Government Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Zoom for Government you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
