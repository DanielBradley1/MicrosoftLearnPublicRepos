<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/lusid-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure LUSID for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate LUSID with Microsoft Entra ID. When you integrate LUSID with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to LUSID.
- Enable your users to be automatically signed-in to LUSID with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- LUSID single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- LUSID supports **SP** and **IDP** initiated SSO.
- LUSID supports **Just In Time** user provisioning.

## Add LUSID from the gallery

To configure the integration of LUSID into Microsoft Entra ID, you need to add LUSID from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **LUSID** in the search box.
4. Select **LUSID** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for LUSID

Configure and test Microsoft Entra SSO with LUSID using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user at LUSID.

To configure and test Microsoft Entra SSO with LUSID, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure LUSID SSO](#configure-lusid-sso)** - to configure the single sign-on settings on application side.

   1. **[Create LUSID test user](#create-lusid-test-user)** - to have a counterpart of B.Simon in LUSID that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **LUSID** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://www.okta.com/saml2/service-provider/<ID>`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://<CustomerDomain>.identity.lusid.com/sso/saml2/<ID>`
6. If you wish to configure the application in **SP** initiated mode, select **Set additional URLs** and type a URL in the **Relay State** text box using the following pattern: `https://<CustomerDomain>.lusid.com/app/home`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL, and Relay State URL. Contact [LUSID support team](mailto:support@finbourne.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. LUSID application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of LUSID application.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

8. In addition to above, LUSID application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | email | user.mail |
   | firstName | user.givenname |
   | lastName | user.surname |
   | fbn-groups | user.assignedroles |


   Note


   Please select [here](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-roles-ui) to know how to configure Role in Microsoft Entra ID.

9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

10. On the **Set up LUSID** section, copy the appropriate URL\(s\) based on your requirement.

    ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure LUSID SSO

To configure single sign-on on **LUSID** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [LUSID support team](mailto:support@finbourne.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create LUSID test user

In this section, a user called B.Simon is created in LUSID. LUSID supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in LUSID, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to LUSID Sign-on URL where you can initiate the login flow.
- Go to LUSID Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the LUSID for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the LUSID tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the LUSID for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure LUSID you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
