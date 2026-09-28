<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/spotinst-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Spotinst for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Spotinst with Microsoft Entra ID. When you integrate Spotinst with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Spotinst.
- Enable your users to be automatically signed-in to Spotinst with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Spotinst single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Spotinst supports **SP and IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Spotinst from the gallery

To configure the integration of Spotinst into Microsoft Entra ID, you need to add Spotinst from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Spotinst** in the search box.
4. Select **Spotinst** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Spotinst

Configure and test Microsoft Entra SSO with Spotinst using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Spotinst.

To configure and test Microsoft Entra SSO with Spotinst, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Spotinst SSO](#configure-spotinst-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Spotinst test user](#create-spotinst-test-user)** - to have a counterpart of B.Simon in Spotinst that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Spotinst** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, if you want to configure the application in IDP initiated mode, perform the following steps:

   1. Make sure **Reply URL** is set to: [https://console.spotinst.com/auth/saml](https://console.spotinst.com/auth/saml).
   2. In **Relay State**, enter your Spotinst Organization ID, which you can also confirm on the **SSO** tab.
   3. **Sign-on URL** must be empty.

6. Select **Save**.
7. Spotinst application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

8. In addition to above, Spotinst application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | Email | user.mail |
   | FirstName | user.givenname |
   | LastName | user.surname |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

10. On the **Set up Spotinst** section, copy the appropriate URL\(s\) based on your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Spotinst SSO

1. In a different web browser window, sign in to Spotinst as a Security Administrator.
2. Select the **user icon** on the top right side of the screen and select **Settings**.

   ![Screenshot shows Settings selected from the User icon.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spotinst-tutorial/settings.png)

3. Select the **SECURITY** tab on the top and then select **Identity Providers** and perform the following steps:

   ![Spotinst security](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spotinst-tutorial/security.png)


   a. Copy the **Relay State** value for your instance and paste it in **Relay State** textbox in **Basic SAML Configuration** section.


   b. Select **BROWSE** to upload the metadata xml file that you have downloaded from Azure portal


   c. Select **SAVE**.

### Create Spotinst test user

The objective of this section is to create a user called Britta Simon in Spotinst.

1. If you have configured the application in the **SP** initiated mode, perform the following steps:

   a. In a different web browser window, sign in to Spotinst as a Security Administrator.

   b. Select the **user icon** on the top right side of the screen and select **Settings**.

   ![Screenshot shows Settings selected from the User icon.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spotinst-tutorial/settings.png)


   c. Select **Users** and select **ADD USER**.


   ![Screenshot shows ADD USER selected from Users.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spotinst-tutorial/add-user.png)


   d. On the add user section, perform the following steps:


   ![Screenshot shows the Add user section where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spotinst-tutorial/new-user.png)


   1. In the **Full Name** textbox, enter the full name of user like `BrittaSimon`.
   2. In the **Email** textbox, enter the email address of the user like `brittasimon@contoso.com`.
   3. Select your organization-specific details for the **Organization Role, Account Role, and Accounts**.

2. If you have configured the application in the **IDP** initiated mode, There's no action item for you in this section. Spotinst supports just-in-time provisioning, which is by default enabled. A new user is created during an attempt to access Spotinst if it doesn't exist yet.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Spotinst Sign on URL where you can initiate the login flow.
- Go to Spotinst Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Spotinst for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Spotinst tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Spotinst for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Spotinst you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
