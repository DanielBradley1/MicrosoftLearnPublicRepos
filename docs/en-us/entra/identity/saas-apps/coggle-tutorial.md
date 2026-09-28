<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/coggle-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Coggle for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Coggle with Microsoft Entra ID. When you integrate Coggle with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Coggle.
- Enable your users to be automatically signed-in to Coggle with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Coggle single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Coggle supports **SP and IDP** initiated SSO.
- Coggle supports **Just In Time** user provisioning.

## Add Coggle from the gallery

To configure the integration of Coggle into Microsoft Entra ID, you need to add Coggle from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Coggle** in the search box.
4. Select **Coggle** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Coggle

Configure and test Microsoft Entra SSO with Coggle using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Coggle.

To configure and test Microsoft Entra SSO with Coggle, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Coggle SSO](#configure-coggle-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Coggle test user](#create-coggle-test-user)** - to have a counterpart of B.Simon in Coggle that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Coggle** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://coggle.it/<TENANT_NAME>/login`

   Note

   The value isn't real. Update the value with the actual Sign-on URL. Contact [Coggle Client support team](mailto:hello@Coggle.it) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. Select **Save**.
8. Coggle application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

9. In addition to above, Coggle application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | firstName | user.givenname |
   | lastName | user.surname |
   | email | user.mail |
10. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

    ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

11. On the **Set up Coggle** section, copy the appropriate URL\(s\) based on your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Coggle SSO

1. In a different browser window, sign on to your Coggle company site as administrator.
2. Select **Coggle** account and select **My Settings**.

   ![Screenshot shows your Coggle company site with My Settings selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/coggle-tutorial/settings.png)

3. Select following **Logo** and select **Authentication**.

   ![Screenshot shows a whale icon and Authentication selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/coggle-tutorial/logo.png)

4. Select **Edit SAML Config**.

   ![Screenshot shows the SAML Integration page with the Edit SAML Config option.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/coggle-tutorial/users.png)

5. On the **SAML Integration** dialog page, perform the following steps:

   ![Screenshot shows the SAML Integration page where you can enter the information in this step.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/coggle-tutorial/certificate.png)


   a. In the **Entrypoint \(ID Provider SSO URL\)** textbox, paste the **Login URL** value, which you copied previously.


   b. Open the downloaded **Certificate \(Base64\)** into Notepad and paste the content into the **Certificate** textbox.


   c. Select **Save**.

### Create Coggle test user

In this section, a user called B.Simon is created in Coggle. Coggle supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Coggle, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Coggle Sign on URL where you can initiate the login flow.
- Go to Coggle Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Coggle for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Coggle tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Coggle for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Coggle you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
