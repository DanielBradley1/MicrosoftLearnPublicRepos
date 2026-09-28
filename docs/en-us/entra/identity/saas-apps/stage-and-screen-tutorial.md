<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/stage-and-screen-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Stage and Screen for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Stage and Screen with Microsoft Entra ID. When you integrate Stage and Screen with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Stage and Screen.
- Enable your users to be automatically signed-in to Stage and Screen with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Stage and Screen single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Stage and Screen support both **SP and IDP** initiated SSO.
- Stage and Screen support **Just In Time** user provisioning.

## Add Stage and Screen from the gallery

To configure the integration of Stage and Screen into Microsoft Entra ID, you need to add Stage and Screen from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Stage and Screen** in the search box.
4. Select **Stage and Screen** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Stage and Screen

Configure and test Microsoft Entra SSO with Stage and Screen using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Stage and Screen.

To configure and test Microsoft Entra SSO with Stage and Screen, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Stage and Screen SSO](#configure-stage-and-screen-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Stage and Screen test user](#create-stage-and-screen-test-user)** - to have a counterpart of B.Simon in Stage and Screen that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Stage and Screen** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Microsoft Entra.
6. Perform the following step, if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** text box, type a URL using the following pattern: `https://portal.stageandscreen.travel/ssosp/spinit?clientid=<Client_ID>`

   Note

   The Sign on URL isn't real. Update the value with the actual Sign-on URL. Contact [Stage and Screen support team](mailto:corporate_support@flightcentre.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
7. Stage and Screen application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows user attributes and claims with default values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Claims")

8. In addition to above, Stage and Screen application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | PortalID | `<ID>` |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Stage and Screen SSO

To configure single sign-on on **Stage and Screen** side, you need to send the **App Federation Metadata Url** to [Stage and Screen support team](mailto:corporate_support@flightcentre.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Stage and Screen test user

In this section, a user called Britta Simon is created in Stage and Screen. Stage and Screen support just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Stage and Screen, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Stage and Screen Sign on URL where you can initiate the login flow.
- Go to Stage and Screen Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application** in Microsoft Entra admin center and you should be automatically signed in to the Stage and Screen for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Stage and Screen tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Stage and Screen for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Stage and Screen you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
