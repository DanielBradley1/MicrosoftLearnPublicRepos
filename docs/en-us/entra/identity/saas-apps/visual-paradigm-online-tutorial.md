<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/visual-paradigm-online-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Visual Paradigm Online for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Visual Paradigm Online with Microsoft Entra ID. When you integrate Visual Paradigm Online with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Visual Paradigm Online.
- Enable your users to be automatically signed-in to Visual Paradigm Online with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Visual Paradigm Online single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Visual Paradigm Online supports **SP** initiated SSO.

## Add Visual Paradigm Online from the gallery

To configure the integration of Visual Paradigm Online into Microsoft Entra ID, you need to add Visual Paradigm Online from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Visual Paradigm Online** in the search box.
4. Select **Visual Paradigm Online** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Visual Paradigm Online

Configure and test Microsoft Entra SSO with Visual Paradigm Online using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Visual Paradigm Online.

To configure and test Microsoft Entra SSO with Visual Paradigm Online, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Visual Paradigm Online SSO](#configure-visual-paradigm-online-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Visual Paradigm Online test user](#create-visual-paradigm-online-test-user)** - to have a counterpart of B.Simon in Visual Paradigm Online that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Visual Paradigm Online** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://online.visual-paradigm.com/w/<Workspace_ID>/saml2`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://online.visual-paradigm.com/w/<Workspace_ID>/saml2/service/`

   c. In the **Sign on URL** text box, type the URL: `https://online.visual-paradigm.com/login.jsp`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Visual Paradigm Online support team](mailto:support@visual-paradigm.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. Your Visual Paradigm Online application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows an example for this. The default value of **Unique User Identifier** is **user.userprincipalname** but Box expects this to be mapped with the user's email address. For that you can use **user.mail** attribute from the list or use the appropriate attribute value based on your organization configuration.

   ![Screenshot shows custom attribute mapping.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attribute")

7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

8. On the **Set up Visual Paradigm Online** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Visual Paradigm Online SSO

To configure single sign-on on **Visual Paradigm Online** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from Microsoft Entra admin center to [Visual Paradigm Online support team](mailto:support@visual-paradigm.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Visual Paradigm Online test user

In this section, you create a user called B.Simon in Visual Paradigm Online. Work with [Visual Paradigm Online support team](mailto:support@visual-paradigm.com) to add the users in the Visual Paradigm Online platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Visual Paradigm Online Sign-on URL where you can initiate the login flow.
- Go to Visual Paradigm Online Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Visual Paradigm Online tile in the My Apps, this option redirects to Visual Paradigm Online Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Visual Paradigm Online you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
