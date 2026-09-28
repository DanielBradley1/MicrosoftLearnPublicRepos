<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/jira52microsoft-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Configure JIRA SAML SSO by Microsoft \(V5.2\) for Single sign-on with Microsoft Entra ID

Warning

**Deprecation notice:** This plugin was deprecated on May 1, 2026. To continue setting up single sign-on for JIRA, use a supported Atlassian SAML integration [here](https://support.atlassian.com/opsgenie/docs/configure-saml-based-sso/) or move to Atlassian Cloud and you can get started [here](https://www.atlassian.com/migration/assess/journey-to-cloud).

In this article,you learn how to integrate JIRA SAML SSO by Microsoft \(V5.2\) with Microsoft Entra ID. When you integrate JIRA SAML SSO by Microsoft \(V5.2\) with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to JIRA SAML SSO by Microsoft \(V5.2\).
- Enable your users to be automatically signed-in to JIRA SAML SSO by Microsoft \(V5.2\) with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Description

Use your Microsoft Entra account with Atlassian JIRA server to enable single sign-on. This way all your organization users can use the Microsoft Entra credentials to sign in into the JIRA application. This plugin uses SAML 2.0 for federation.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- JIRA Core and Software 5.2 should installed and configured on Windows 64-bit version.
- JIRA server is HTTPS enabled.
- Note the supported versions for JIRA Plugin are mentioned in below section.
- JIRA server is reachable on internet particularly to Microsoft Entra Login page for authentication and should able to receive the token from Microsoft Entra ID.
- Admin credentials are set up in JIRA.
- WebSudo is disabled in JIRA.
- Test user created in the JIRA server application.

Note

To test the steps in this article, we don't recommend using a production environment of JIRA. Test the integration first in development or staging environment of the application and then use the production environment.

To test the steps in this article, you should follow these recommendations:

- Don't use your production environment, unless it's necessary.
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

## Supported versions of JIRA

- JIRA Core and Software: 5.2.
- JIRA also supports 6.0 to 7.12. For more details, select [JIRA SAML SSO by Microsoft](https://learn.microsoft.com/en-us/entra/identity/saas-apps/jiramicrosoft-tutorial).

Note

Please note that our JIRA Plugin also works on Ubuntu Version 16.04.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- JIRA SAML SSO by Microsoft \(V5.2\) supports **SP** initiated SSO.

## Adding JIRA SAML SSO by Microsoft \(V5.2\) from the gallery

To configure the integration of JIRA SAML SSO by Microsoft \(V5.2\) into Microsoft Entra ID, you need to add JIRA SAML SSO by Microsoft \(V5.2\) from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **JIRA SAML SSO by Microsoft \(V5.2\)** in the search box.
4. Select **JIRA SAML SSO by Microsoft \(V5.2\)** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for JIRA SAML SSO by Microsoft \(V5.2\)

In this section, you configure and test Microsoft Entra single sign-on with JIRA SAML SSO by Microsoft \(V5.2\) based on a test user named **Britta Simon**. For single sign-on to work, you must establish a linked relationship between a Microsoft Entra user and the related user in JIRA SAML SSO by Microsoft \(V5.2\).

To configure and test Microsoft Entra single sign-on with JIRA SAML SSO by Microsoft \(V5.2\), perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
   2. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.

2. **[Configure JIRA SAML SSO by Microsoft \(V5.2\) SSO](#configure-jira-saml-sso-by-microsoft-v52-sso)** - to configure the Single Sign-On settings on application side.

   1. **[Create JIRA SAML SSO by Microsoft \(V5.2\) test user](#create-jira-saml-sso-by-microsoft-v52-test-user)** - to have a counterpart of Britta Simon in JIRA SAML SSO by Microsoft \(V5.2\) that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

### Configure Microsoft Entra SSO

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **JIRA SAML SSO by Microsoft \(V5.2\)** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a Single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** box, type a URL using the following pattern: `https://<domain:port>/`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<domain:port>/plugins/servlet/saml/auth`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<domain:port>/plugins/servlet/saml/auth`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-On URL. Port is optional in case it’s a named URL. These values are received during the configuration of Jira plugin, which is explained later in the article.
6. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure JIRA SAML SSO by Microsoft \(V5.2\) SSO

1. In a different web browser window, sign in to your JIRA instance as an administrator.
2. Hover on cog and select the **Add-ons**.

   ![Screenshot shows Add-ons selected from the Settings menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/menu.png)

3. Under Add-ons tab section, select **Manage add-ons**.

   ![Screenshot shows Manage add-ons selected in the Add-ons tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/dashboard.png)

4. Download the plugin from [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=56521). Manually upload the plugin provided by Microsoft using **Upload add-on** menu. The download of plugin is covered under [Microsoft Service Agreement](https://www.microsoft.com/servicesagreement/).

   ![Screenshot shows Manage add-ons with the Upload add-on link called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/service.png)

5. Once the plugin is installed, it appears in **User Installed** add-ons section. Select **Configure** to configure the new plugin.
6. Perform the following steps on configuration page:

   ![Screenshot shows the Microsoft Jira S S O Connector configuration page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/configuration.png)


   Tip


   Ensure that there is only one certificate mapped against the app so that there is no error in resolving the metadata. If there are multiple certificates, upon resolving the metadata, admin gets an error.


   a. In **Metadata URL** textbox, paste **App Federation Metadata Url** value which you have copied and select the **Resolve** button. It reads the IdP metadata URL and populates all the fields information.


   b. Copy the **Identifier, Reply URL and Sign on URL** values and paste them in **Identifier, Reply URL and Sign on URL** textboxes respectively in **Basic SAML Configuration** section.


   c. In **Login Button Name** type the name of button your organization wants the users to see on login screen.


   d. In **SAML User ID Locations** select either **User ID is in the NameIdentifier element of the Subject statement** or **User ID is in an Attribute element**. This ID has to be the JIRA user ID. If the user ID isn't matched, then system doesn't allow users to sign in.


   Note


   Default SAML User ID location is Name Identifier. You can change this to an attribute option and enter the appropriate attribute name.


   e. If you select **User ID is in an Attribute element** option, then in **Attribute name** textbox type the name of the attribute where User ID is expected.


   f. If you're using the federated domain \(like ADFS, and so on\) with Microsoft Entra ID, then select the **Enable Home Realm Discovery** option and configure the **Domain Name**.


   g. In **Domain Name** type the domain name here in case of the ADFS-based login.


   h. Check **Enable Single Sign out** if you wish to sign out from Microsoft Entra ID when a user signs out from JIRA.


   i. Select **Save** button to save the settings.


   Note


   For more information about installation and troubleshooting, visit [MS JIRA SSO Connector Admin Guide](https://learn.microsoft.com/en-us/entra/identity/saas-apps/ms-confluence-jira-plugin-adminguide) and there is also [FAQ](https://learn.microsoft.com/en-us/entra/identity/saas-apps/ms-confluence-jira-plugin-adminguide) for your assistance.

### Create JIRA SAML SSO by Microsoft \(V5.2\) test user

To enable Microsoft Entra users to sign in to JIRA on-premises server, they must be provisioned into JIRA on-premises server.

**To provision a user account, perform the following steps:**

1. Sign in to your JIRA on-premises server as an administrator.
2. Hover on cog and select the **User management**.

   ![Screenshot shows User management selected from the Settings menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/user.png)

3. You're redirected to Administrator Access page to enter **Password** and select **Confirm** button.

   ![Screenshot shows Administrator Access page where you enter your credentials.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/access.png)

4. Under **User management** tab section, select **create user**.

   ![Screenshot shows the User management tab where you can Create user.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/create-user.png)

5. On the **“Create new user”** dialog page, perform the following steps:

   ![Screenshot shows the Create new user dialog box where you can enter the information in this step.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jira52microsoft-tutorial/new-user.png)


   a. In the **Email address** textbox, type the email address of user like Brittasimon@contoso.com.


   b. In the **Full Name** textbox, type full name of the user like Britta Simon.


   c. In the **Username** textbox, type the email of user like Brittasimon@contoso.com.


   d. In the **Password** textbox, type the password of user.


   e. Select **Create user**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to JIRA SAML SSO by Microsoft \(V5.2\) Sign-on URL where you can initiate the login flow.
- Go to JIRA SAML SSO by Microsoft \(V5.2\) Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the JIRA SAML SSO by Microsoft \(V5.2\) tile in the My Apps, this option redirects to JIRA SAML SSO by Microsoft \(V5.2\) Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure JIRA SAML SSO by Microsoft \(V5.2\) you can enforce Session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
