<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/articulate360-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Articulate 360 for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Articulate 360 with Microsoft Entra ID. When you integrate Articulate 360 with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Articulate 360.
- Enable your users to be automatically signed-in to Articulate 360 with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Articulate 360 single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Articulate 360 supports **SP** and **IDP** initiated SSO.

## Add Articulate 360 from the gallery

To configure the integration of Articulate 360 into Microsoft Entra ID, you need to add Articulate 360 from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Articulate 360** in the search box.
4. Select **Articulate 360** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Articulate 360

Configure and test Microsoft Entra SSO with Articulate 360 using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Articulate 360.

To configure and test Microsoft Entra SSO with Articulate 360, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Articulate 360 SSO](#configure-articulate-360-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Articulate 360 test user](#create-articulate-360-test-user)** - to have a counterpart of B.Simon in Articulate 360 that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Articulate 360** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://www.okta.com/saml2/service-provider/<SAMPLE>`

   b. In the **Reply URL** textbox, type the URL: `https://id.articulate.com/sso/saml2`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://id.articulate.com/`

   Note

   The Identifier value isn't real. Update this value with the actual Identifier. Contact [Articulate 360 support team](mailto:enterprise@articulate.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. Articulate 360 application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

8. Articulate 360 application expects the default attributes to be replaced with the specific attributes as shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | firstName | user.givenname |
   | lastName | user.surname |
   | email | user.mail |
9. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

10. On the **Set up Articulate 360** section, copy the appropriate URL\(s\) based on your requirement.

    ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Attributes")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Articulate 360 SSO

To configure single sign-on on **Articulate 360** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Articulate 360 support team](mailto:enterprise@articulate.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Articulate 360 test user

In this section, a user called B.Simon is created in Articulate 360. Articulate 360 supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Articulate 360, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Articulate 360 Sign-On URL where you can initiate the login flow.
- Go to Articulate 360 Sign-On URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Articulate 360 for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Articulate 360 tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Articulate 360 for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Articulate 360 you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
