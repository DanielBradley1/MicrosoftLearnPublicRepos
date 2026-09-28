<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/tigertext-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure TigerConnect Secure Messenger for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate TigerConnect Secure Messenger with Microsoft Entra ID. When you integrate TigerConnect Secure Messenger with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to TigerConnect Secure Messenger.
- Enable your users to be automatically signed-in to TigerConnect Secure Messenger with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A TigerConnect Secure Messenger subscription with single sign-on enabled.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment and integrate TigerConnect Secure Messenger with Microsoft Entra ID.

- TigerConnect Secure Messenger supports **SP** initiated SSO.

## Add TigerConnect Secure Messenger from the gallery

To configure the integration of TigerConnect Secure Messenger into Microsoft Entra ID, you need to add TigerConnect Secure Messenger from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **TigerConnect Secure Messenger** in the search box.
4. Select **TigerConnect Secure Messenger** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for TigerConnect Secure Messenger

In this section, you configure and test Microsoft Entra single sign-on with TigerConnect Secure Messenger based on a test user named **Britta Simon**. For single sign-on to work, you must establish a link between a Microsoft Entra user and the related user in TigerConnect Secure Messenger.

To configure and test Microsoft Entra single sign-on with TigerConnect Secure Messenger, you need to perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with Britta Simon.
   2. **Assign the Microsoft Entra test user** to enable Britta Simon to use Microsoft Entra single sign-on.

2. **[Configure TigerConnect Secure Messenger SSO](#configure-tigerconnect-secure-messenger-sso)** to configure the single sign-on settings on the application side.

   1. **[Create a TigerConnect Secure Messenger test user](#create-a-tigerconnect-secure-messenger-test-user)** so that there's a user named Britta Simon in TigerConnect Secure Messenger who's linked to the Microsoft Entra user named Britta Simon.

3. **[Test SSO](#test-sso)** to verify whether the configuration works.

## Configure Microsoft Entra SSO

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with TigerConnect Secure Messenger, take the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **TigerConnect Secure Messenger** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, perform the following steps:

   1. In the **Sign on URL** box, type the URL:

      `https://home.tigertext.com`
   2. In the **Identifier \(Entity ID\)** box, type a URL by using the following pattern:

      `https://saml-lb.tigertext.me/v1/organization/<INSTANCE_ID>`


   Note


   The **Identifier \(Entity ID\)** value isn't real. Update this value with the actual identifier. To get the value, contact the [TigerConnect Secure Messenger support team](mailto:prosupport@tigertext.com). You can also refer to the patterns shown in the **Basic SAML Configuration** pane.

6. On the **Set up Single Sign-On with SAML** pane, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options and save it on your computer.

   ![The Federation Metadata XML download option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. In the **Set up TigerConnect Secure Messenger** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure TigerConnect Secure Messenger SSO

To configure single sign-on on the TigerConnect Secure Messenger side, you need to send the downloaded Federation Metadata XML and the appropriate copied URLs to the [TigerConnect Secure Messenger support team](mailto:prosupport@tigertext.com). The TigerConnect Secure Messenger team will make sure the SAML SSO connection is set properly on both sides.

## Create a TigerConnect Secure Messenger test user

In this section, you create a user called Britta Simon in TigerConnect Secure Messenger. Work with the [TigerConnect Secure Messenger support team](mailto:prosupport@tigertext.com) to add Britta Simon as a user in TigerConnect Secure Messenger. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to TigerConnect Secure Messenger Sign-on URL where you can initiate the login flow.
- Go to TigerConnect Secure Messenger Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the TigerConnect Secure Messenger tile in the My Apps, this option redirects to TigerConnect Secure Messenger Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure TigerConnect Secure Messenger you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
