<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cpqsync-by-cincom-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Cincom CPQ for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Cincom CPQ with Microsoft Entra ID. When you integrate Cincom CPQ with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Cincom CPQ.
- Enable your users to be automatically signed-in to Cincom CPQ with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Cincom CPQ single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Cincom CPQ supports **SP and IDP** initiated SSO.

## Add Cincom CPQ from the gallery

To configure the integration of Cincom CPQ into Microsoft Entra ID, you need to add Cincom CPQ from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Cincom CPQ** in the search box.
4. Select **Cincom CPQ** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Cincom CPQ

Configure and test Microsoft Entra SSO with Cincom CPQ using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Cincom CPQ.

To configure and test Microsoft Entra SSO with Cincom CPQ, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Cincom CPQ SSO](#configure-cincom-cpq-sso)** - to configure the Single Sign-On settings on application side.

   1. **[Create Cincom CPQ test user](#create-cincom-cpq-test-user)** - to have a counterpart of B.Simon in Cincom CPQ that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cincom CPQ** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a Single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://cincom.oktapreview.com/sso/saml2/<CUSTOMURL>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://cincom.okta.com/sso/saml2/<CUSTOMDOMAIN>`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://cincom.okta.com/`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Cincom CPQ Client support team](https://supportweb.cincom.com/default.aspx) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png "Certificate")

8. On the **Set up Cincom CPQ** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Cincom CPQ SSO

To configure single sign-on on **Cincom CPQ** side, you need to send the downloaded **Certificate \(Raw\)** and appropriate copied URLs from the application configuration to [Cincom CPQ support team](https://supportweb.cincom.com/default.aspx). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Cincom CPQ test user

In this section, you create a user called B.Simon in Cincom CPQ. Work with [Cincom CPQ support team](https://supportweb.cincom.com/default.aspx) to add the users in the Cincom CPQ platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Cincom CPQ Sign-On URL where you can initiate the login flow.
- Go to Cincom CPQ Sign-On URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Cincom CPQ for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Cincom CPQ tile in the My Apps, if configured in SP mode you would be redirected to the application Sign-On page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Cincom CPQ for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Cincom CPQ you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
