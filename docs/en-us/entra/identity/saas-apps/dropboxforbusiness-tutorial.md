<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/dropboxforbusiness-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Configure Dropbox Business for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Dropbox Business with Microsoft Entra ID. When you integrate Dropbox Business with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Dropbox Business.
- Enable your users to be automatically signed-in to Dropbox Business with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Dropbox Business is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Dropbox Business single sign-on \(SSO\) enabled subscription.

## Scenario description

- In this article, you configure and test Microsoft Entra SSO in a test environment. Dropbox Business supports **SP** initiated SSO.
- Dropbox Business supports [Automated user provisioning and deprovisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/dropboxforbusiness-provisioning-tutorial).

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Dropbox Business from the gallery

To configure the integration of Dropbox Business into Microsoft Entra ID, you need to add Dropbox Business from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Dropbox Business** in the search box.
4. Select **Dropbox Business** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Dropbox Business

Configure and test Microsoft Entra SSO with Dropbox Business using a test user called **Britta Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Dropbox Business.

To configure and test Microsoft Entra SSO with Dropbox Business, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
   2. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.

2. **[Configure Dropbox Business SSO](#configure-dropbox-business-sso)** - to configure the Single Sign-On settings on application side.

   1. **[Create Dropbox Business test user](#create-dropbox-business-test-user)** - to have a counterpart of Britta Simon in Dropbox Business that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Dropbox Business** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a Single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** page, enter the values for the following fields:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://www.dropbox.com/sso/<id>`

   b. In the **Identifier \(Entity ID\)** text box, type the value: `Dropbox`

   c. In the **Reply URL** field, enter `https://www.dropbox.com/saml_login`

   Note

   The **Dropbox Sign SSO ID** can be found in the Dropbox site at Dropbox > Admin console > Settings > Single sign-on > SSO sign-in URL.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Dropbox Business** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Dropbox Business SSO

1. In a different web browser window, sign in to your Dropbox Business company site as an administrator

   ![Screenshot that shows the "Dropbox Business Sign in" page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/account.png "Configure single sign-on")

2. Select the **User Icon** and select **Settings** tab.

   ![Screenshot that shows the "USER ICON" action and "Settings" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/user-icon.png "Configure single sign-on")

3. In the navigation pane on the left side, select **Admin console**.

   ![Screenshot that shows "Admin console" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/admin-console.png "Configure single sign-on")

4. On the **Admin console**, select **Settings** in the left navigation pane.

   ![Screenshot that shows "Settings" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/settings.png "Configure single sign-on")

5. Select **Single sign-on** option under the **Authentication** section.

   ![Screenshot that shows the "Authentication" section with "Single sign-on" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/authentication.png "Configure single sign-on")

6. In the **Single sign-on** section, perform the following steps:

   ![Screenshot that shows the "Single sign-on" configuration settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/configure-sso.png "Configure single sign-on")


   a. Select **Required** as an option from the dropdown for the **Single sign-on**.


   b. Select **Add sign-in URL** and in the **Identity provider sign-in URL** textbox, paste the **Login URL** value which you have copied and then select **Done**.


   ![Configure single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/sso.png "Configure single sign-on")


   c. Select **Upload certificate**, and then browse to your **Base64 encoded certificate file** which you have downloaded.


   d. Select **Copy link** and paste the copied value into the **Sign-on URL** textbox of **Dropbox Business Domain and URLs** section on Azure portal.


   e. Select **Save**.

### Create Dropbox Business test user

1. Log in to the Dropbox Business website as an administrator.
2. Go to the **Admin Console** and select **Members** in the left menu.

   ![Screenshot for Invite member](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/invite-member.png)

3. Enter the valid user email to add the user and select **Invite**.

   ![Screenshot for Invite](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dropboxforbusiness-tutorial/invite-button.png)

This application also supports automatic user provisioning. See how to enable auto provisioning for [Dropbox Business](https://learn.microsoft.com/en-us/entra/identity/saas-apps/dropboxforbusiness-provisioning-tutorial).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Dropbox Business Sign-on URL where you can initiate the login flow.
- Go to Dropbox Business Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Dropbox Business tile in the My Apps, this option redirects to Dropbox Business Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Dropbox Business you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
