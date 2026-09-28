<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/saucelabs-mobileandwebtesting-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Sauce Labs - Mobile and Web Testing for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Sauce Labs - Mobile and Web Testing with Microsoft Entra ID. When you integrate Sauce Labs - Mobile and Web Testing with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Sauce Labs - Mobile and Web Testing.
- Enable your users to be automatically signed-in to Sauce Labs - Mobile and Web Testing with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Sauce Labs - Mobile and Web Testing single sign-on enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Sauce Labs - Mobile and Web Testing supports **IDP** initiated SSO.
- Sauce Labs - Mobile and Web Testing supports **Just In Time** user provisioning.

## Add Sauce Labs - Mobile and Web Testing from the gallery

To configure the integration of Sauce Labs - Mobile and Web Testing into Microsoft Entra ID, you need to add Sauce Labs - Mobile and Web Testing from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Sauce Labs - Mobile and Web Testing** in the search box.
4. Select **Sauce Labs - Mobile and Web Testing** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Sauce Labs - Mobile and Web Testing

Configure and test Microsoft Entra SSO with Sauce Labs - Mobile and Web Testing using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Sauce Labs - Mobile and Web Testing.

To configure and test Microsoft Entra SSO with Sauce Labs - Mobile and Web Testing, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Sauce Labs - Mobile and Web Testing SSO](#configure-sauce-labs---mobile-and-web-testing-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Sauce Labs - Mobile and Web Testing test user](#create-sauce-labs---mobile-and-web-testing-test-user)** - to have a counterpart of B.Simon in Sauce Labs - Mobile and Web Testing that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Sauce Labs - Mobile and Web Testing** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up Sauce Labs - Mobile and Web Testing** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Sauce Labs - Mobile and Web Testing SSO

1. In a different web browser window, sign in to your Sauce Labs - Mobile and Web Testing company site as an administrator.
2. Select the **Account** dropdown and select the **Team Management** tab.

   ![Screenshot that shows the Account dropdown and Team Management dropdown item selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saucelabs-mobileandwebtesting-tutorial/user.png)
3. Select **View Settings** under **Organization Settings**.

   ![Screenshot that shows the View Settings button in the Organization Settings box.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saucelabs-mobileandwebtesting-tutorial/org-settings.png)
4. Select the **Single Sign-On** tab.

   ![Screenshot that shows the Single Sign-On tab selected under Organization Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saucelabs-mobileandwebtesting-tutorial/configure.png)
5. In the **Single Sign-On** section, perform the following steps.

   ![Screenshot that shows selecting options on the Single Sign-On tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saucelabs-mobileandwebtesting-tutorial/browse.png)

   1. Define your Unique Identifier String \(UIS\) and select **Save**.
   2. Select **Upload New Metadata File** and upload the downloaded metadata file from Microsoft Entra ID.
   3. Under **Enable Single Sign-On**, select **Enabled**.

### Create Sauce Labs - Mobile and Web Testing test user

In this section, a user called B.Simon is created in Sauce Labs - Mobile and Web Testing. Sauce Labs - Mobile and Web Testing supports just-in-time user provisioning, which is always enabled. There's no action item for you in this section. If a user doesn't already exist in Sauce Labs - Mobile and Web Testing, a new one is created after authentication.

Note

If you need to create a user manually, contact [Sauce Labs - Mobile and Web Testing support team](mailto:support@saucelabs.com).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Sauce Labs - Mobile and Web Testing for which you set up the SSO.
- You can use Microsoft My Apps. When you select the Sauce Labs - Mobile and Web Testing tile in the My Apps, you should be automatically signed in to the Sauce Labs - Mobile and Web Testing for which you set up the SSO. For more information about My Apps, see [Introduction to My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Sauce Labs - Mobile and Web Testing you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
