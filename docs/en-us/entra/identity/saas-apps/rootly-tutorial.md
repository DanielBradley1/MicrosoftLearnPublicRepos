<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/rootly-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Rootly for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Rootly with Microsoft Entra ID. When you integrate Rootly with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Rootly.
- Enable your users to be automatically signed-in to Rootly with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Rootly single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Rootly supports **SP** and **IDP** initiated SSO.
- Rootly supports **Just In Time** user provisioning.
- Rootly supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/rootly-provisioning-tutorial).

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Rootly from the gallery

To configure the integration of Rootly into Microsoft Entra ID, you need to add Rootly from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Rootly** in the search box.
4. Select **Rootly** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Rootly

Configure and test Microsoft Entra SSO with Rootly using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Rootly.

To configure and test Microsoft Entra SSO with Rootly, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Rootly SSO](#configure-rootly-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Rootly test user](#create-rootly-test-user)** - to have a counterpart of B.Simon in Rootly that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Rootly** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.
6. \(Optional\) Perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://rootly.com/sso`
7. Rootly application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of Rootly application.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

8. In addition to above, Rootly application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | firstname | user.displayname |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(PEM\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificate-base64-download.png "Certificate")

10. On the **Set up Rootly** section, copy the appropriate URL\(s\) based on your requirement.

    ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Rootly SSO

Use the previously copied URL\(s\) and PEM Certificate to configure single sign-on on **Rootly** side.

1. Identity Provider ID: `Microsoft Entra Identifier`
2. Identity Login URL: `Your Login URL`
3. Identity Logout Url: `Your Login URL`
4. IDP Certificate: `Content of your Certificate PEM file`
5. Domain Names: `Your company domain used for SSO`

Now go ahead Enable `Enable and require SSO` and Save your SSO setup in Rootly.

### Create Rootly test user

In this section, a user called B.Simon is created in Rootly. Rootly supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Rootly, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Rootly Sign-On URL where you can initiate the login flow.
- Go to Rootly Sign-On URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Rootly for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Rootly tile in the My Apps, if configured in SP mode you would be redirected to the application Sign-On page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Rootly for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Rootly you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
