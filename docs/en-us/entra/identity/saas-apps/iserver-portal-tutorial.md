<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/iserver-portal-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure iServer Portal for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate iServer Portal with Microsoft Entra ID. When you integrate iServer Portal with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to iServer Portal.
- Enable your users to be automatically signed-in to iServer Portal with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- iServer Portal single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- iServer Portal supports **SP and IDP** initiated SSO.

## Add iServer Portal from the gallery

To configure the integration of iServer Portal into Microsoft Entra ID, you need to add iServer Portal from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **iServer Portal** in the search box.
4. Select **iServer Portal** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for iServer Portal

Configure and test Microsoft Entra SSO with iServer Portal using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in iServer Portal.

To configure and test Microsoft Entra SSO with iServer Portal, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure iServer Portal SSO](#configure-iserver-portal-sso)** - to configure the single sign-on settings on application side.

   1. **[Create iServer Portal test user](#create-iserver-portal-test-user)** - to have a counterpart of B.Simon in iServer Portal that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **iServer Portal** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a value using the following pattern: `iserver-portal-<myiserverportal>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<myiserverportal.com>/SAML/login`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<myiserverportal.com>/SAML/login`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [iServer Portal Client support team](mailto:support@orbussoftware.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. In the **SAML Signing Certificate** section, select **Edit** button to open **SAML Signing Certificate** dialog.

   ![Screenshot shows to Edit SAML Signing Certificate.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-certificate.png "Certificate")

8. In the **SAML Signing Certificate** section, copy the **Thumbprint Value** and save it on your computer.

   ![Screenshot shows to Copy Thumbprint value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-thumbprint.png "Values")

9. On the **Set up iServer Portal** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure iServer Portal SSO

To configure single sign-on on **iServer Portal** side, you need to send the **Thumbprint Value** and appropriate copied URLs from the application configuration to [iServer Portal support team](mailto:support@orbussoftware.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create iServer Portal test user

In this section, you create a user called B.Simon in iServer Portal. Work with [iServer Portal support team](mailto:support@orbussoftware.com) to add the users in the iServer Portal platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to iServer Portal Sign-On URL where you can initiate the login flow.
- Go to iServer Portal Sign-On URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the iServer Portal for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the iServer Portal tile in the My Apps, if configured in SP mode you would be redirected to the application Sign-On page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the iServer Portal for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure iServer Portal you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
