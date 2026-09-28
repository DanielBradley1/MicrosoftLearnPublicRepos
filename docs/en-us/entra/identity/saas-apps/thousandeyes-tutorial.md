<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/thousandeyes-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure ThousandEyes for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate ThousandEyes with Microsoft Entra ID. When you integrate ThousandEyes with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to ThousandEyes.
- Enable your users to be automatically signed-in to ThousandEyes with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- ThousandEyes single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- ThousandEyes supports **SP and IDP** initiated SSO.
- ThousandEyes supports [**Automated** user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/thousandeyes-provisioning-tutorial).

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add ThousandEyes from the gallery

To configure the integration of ThousandEyes into Microsoft Entra ID, you need to add ThousandEyes from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **ThousandEyes** in the search box.
4. Select **ThousandEyes** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for ThousandEyes

Configure and test Microsoft Entra SSO with ThousandEyes using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in ThousandEyes.

To configure and test Microsoft Entra SSO with ThousandEyes, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure ThousandEyes SSO](#configure-thousandeyes-sso)** - to configure the single sign-on settings on application side.

   1. **[Create ThousandEyes test user](#create-thousandeyes-test-user)** - to have a counterpart of B.Simon in ThousandEyes that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **ThousandEyes** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the application is pre-configured and the necessary URLs are already pre-populated with Azure. The user needs to save the configuration by selecting the **Save** button.
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://app.thousandeyes.com/login/sso`
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. On the **Set up ThousandEyes** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure ThousandEyes SSO

1. In a different web browser window, sign on to your **ThousandEyes** company site as an administrator.
2. In the menu on the top, select **Settings**.

   ![Screenshot shows the ThousandEyes site with Settings selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/settings-tab.png "Settings")

3. Select **Account**

   ![Screenshot shows Account selected from the Settings menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/menu.png "Account")

4. Select the **Security & Authentication** tab.

   ![Security & Authentication](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/security.png "Security & Authentication")

5. In the **Setup Single Sign-On** section, perform the following steps:

   ![Setup Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/configuration.png "Setup Single Sign-On")


   a. Select **Enable Single Sign-On**.


   b. In **Login Page URL** textbox, paste **Login URL**.


   c. In **Logout Page URL** textbox, paste **Logout URL**.


   d. **Identity Provider Issuer** textbox, paste **Microsoft Entra Identifier**.


   e. In **Verification Certificate**, select **Choose file**, and then upload the certificate you have downloaded previously.


   f. Select **Save**.

### Create ThousandEyes test user

The objective of this section is to create a user called Britta Simon in ThousandEyes. ThousandEyes supports automatic user provisioning, which is by default enabled. You can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/thousandeyes-provisioning-tutorial) on how to configure automatic user provisioning.

**If you need to create user manually, perform following steps:**

1. Sign in to your ThousandEyes company site as an administrator.
2. Select **Settings**.

   ![Screenshot shows the ThousandEyes site with Settings selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/settings-tab.png "Settings")

3. Select **Account**.

   ![Screenshot shows Account selected from the Settings menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/menu.png "Account")

4. Select the **Accounts & Users** tab.

   ![Accounts & Users](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/user.png "Accounts & Users")

5. In the **Add Users & Accounts** section, perform the following steps:

   ![Add User Accounts](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/thousandeyes-tutorial/add-user.png "Add User Accounts")


   a. In **Name** textbox, type the name of user like **B.Simon**.


   b. In **Email** textbox, type the email of user like b.simon@contoso.com.


   b. Select **Add New User to Account**.


   Note


   The Microsoft Entra account holder gets an email including a link to confirm and activate the account.

Note

You can use any other ThousandEyes user account creation tools or APIs provided by ThousandEyes to provision Microsoft Entra user accounts.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to ThousandEyes Sign on URL where you can initiate the login flow.
- Go to ThousandEyes Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the ThousandEyes for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the ThousandEyes tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the ThousandEyes for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure ThousandEyes you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
