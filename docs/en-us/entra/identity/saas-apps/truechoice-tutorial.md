<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/truechoice-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure TrueChoice for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate TrueChoice with Microsoft Entra ID. When you integrate TrueChoice with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to TrueChoice.
- Enable your users to be automatically signed-in to TrueChoice with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- TrueChoice single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- TrueChoice supports **SP** initiated SSO.
- TrueChoice supports **Just In Time** user provisioning.

## Adding TrueChoice from the gallery

To configure the integration of TrueChoice into Microsoft Entra ID, you need to add TrueChoice from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **TrueChoice** in the search box.
4. Select **TrueChoice** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for TrueChoice

Configure and test Microsoft Entra SSO with TrueChoice using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in TrueChoice.

To configure and test Microsoft Entra SSO with TrueChoice, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure TrueChoice SSO](#configure-truechoice-sso)** - to configure the single sign-on settings on application side.

   1. **[Create TrueChoice test user](#create-truechoice-test-user)** - to have a counterpart of B.Simon in TrueChoice that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **TrueChoice** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `urn:amazon:cognito:sp:<TRUECHOICE_APPID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<APP>.auth.us-east-2.amazoncognito.com/saml2/idpresponse`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://<APP>.auth.us-east-2.amazoncognito.com/login?response_type=code&client_id=<ID>&redirect_uri=https://<APP_ID>.amplifyapp.com/auth/`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [TrueChoice Client support team](mailto:helpdesk@truechoice.io) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. TrueChoice application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/truechoice-tutorial/default-attributes.png)

7. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure TrueChoice SSO

To configure single sign-on on **TrueChoice** side, you need to send the **App Federation Metadata Url** to [TrueChoice support team](mailto:helpdesk@truechoice.io). They set this setting to have the SAML SSO connection set properly on both sides.

### Create TrueChoice test user

In this section, a user called Britta Simon is created in TrueChoice. TrueChoice supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in TrueChoice, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to TrueChoice Sign-on URL where you can initiate the login flow.
- Go to TrueChoice Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the TrueChoice tile in the My Apps, this option redirects to TrueChoice Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure TrueChoice you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
