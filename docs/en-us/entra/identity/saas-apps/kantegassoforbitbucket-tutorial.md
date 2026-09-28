<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/kantegassoforbitbucket-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Kantega SSO for Bitbucket for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Kantega SSO for Bitbucket with Microsoft Entra ID. When you integrate Kantega SSO for Bitbucket with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Kantega SSO for Bitbucket.
- Enable your users to be automatically signed-in to Kantega SSO for Bitbucket with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Kantega SSO for Bitbucket single sign-on enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Kantega SSO for Bitbucket supports **SP and IDP** initiated SSO.

## Add Kantega SSO for Bitbucket from the gallery

To configure the integration of Kantega SSO for Bitbucket into Microsoft Entra ID, you need to add Kantega SSO for Bitbucket from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Kantega SSO for Bitbucket** in the search box.
4. Select **Kantega SSO for Bitbucket** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Kantega SSO for Bitbucket

Configure and test Microsoft Entra SSO with Kantega SSO for Bitbucket using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Kantega SSO for Bitbucket.

To configure and test Microsoft Entra SSO with Kantega SSO for Bitbucket, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Kantega SSO for Bitbucket SSO](#configure-kantega-sso-for-bitbucket-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Kantega SSO for Bitbucket test user](#create-kantega-sso-for-bitbucket-test-user)** - to have a counterpart of B.Simon in Kantega SSO for Bitbucket that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Kantega SSO for Bitbucket** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, If you wish to configure the application in **IDP** initiated mode, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<server-base-url>/plugins/servlet/no.kantega.saml/sp/<uniqueid>/login`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<server-base-url>/plugins/servlet/no.kantega.saml/sp/<uniqueid>/login`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<server-base-url>/plugins/servlet/no.kantega.saml/sp/<uniqueid>/login`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL, and Sign-On URL. These values are received during the configuration of Bitbucket plugin which is explained later in the article.
7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up Kantega SSO for Bitbucket** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Kantega SSO for Bitbucket SSO

1. In a different web browser window, sign in to your Bitbucket admin portal as an administrator.
2. Select cog and select the **Find new add-ons**.

   ![Screenshot shows BitBucket Administration with Find new add-ons selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/admin.png)

3. Search **Kantega SSO for Bitbucket SAML & Kerberos** and select **Install** button to install the new SAML plugin.

   ![Screenshot shows Kantega SSO for Bitbucket SAML & Kerberos with the option to install.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/menu.png)

4. The plugin installation starts.

   ![Screenshot shows Installing progress.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/installation.png)

5. Once the installation is complete. Select **Close**.

   ![Screenshot shows the Close button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/license.png)

6. In the **Kantega SSO for Bitbucket SAML Kerberos** page, select **Manage**.
7. Select **Configure** to configure the new plugin.

   ![Screenshot shows User-installed add-ons with Configure selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/profile.png)

8. In the **SAML** section, select **Microsoft Entra ID** from the **Add identity provider** dropdown.
9. In the **Kantega Single Sign-on** page, select **Basic**.
10. On the **App properties** section, perform following steps:

    ![Screenshot shows the App properties section where you can provide the information in this step.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/properties.png)


    a. Copy the **App ID URI** value and use it as **Identifier, Reply URL, and Sign-On URL** on the **Basic SAML Configuration** section in Azure portal.


    b. Select **Next**.

11. On the **Metadata import** section, select **Metadata file on my computer**.
12. Select **Browse file** to upload the metadata file that you previously downloaded, then select **Next**.
13. On the **Name and SSO location** section, perform following steps:

    ![Screenshot shows the Name and S S O location where Microsoft Entra ID is the identity provider name.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/location.png)


    a. Add Name of the Identity Provider in **Identity provider name** textbox \(such as Microsoft Entra ID\).


    b. Select **Next**.

14. Verify the Signing certificate and select **Next**.

    ![Screenshot shows Signature verification.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/certificate.png)

15. On the **Bitbucket user accounts** section, perform following steps:

    ![Screenshot shows BitBucket user accounts where you have the option to create users.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/accounts.png)


    a. Select **Create users in Bitbucket's internal Directory if needed** and enter the appropriate name of the group for users \(can be multiple no. of groups separated by comma\).


    b. Select **Next**.

16. Select **Finish**.
17. On the **Known domains for Microsoft Entra ID** section, perform following steps:

    a. Select **Known domains** from the left panel of the page.

    b. Enter domain name in the **Known domains** textbox.

    c. Select **Save**.

### Create Kantega SSO for Bitbucket test user

To enable Microsoft Entra users to sign in to Bitbucket, they must be provisioned into Bitbucket. In case of Kantega SSO for Bitbucket, provisioning is a manual task.

**To provision a user account, perform the following steps:**

1. Sign in to your Bitbucket company site as an administrator.
2. Select settings icon.

   ![Screenshot shows the Settings icon.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/user.png)

3. Under **Administration** tab section, select **Users**.

   ![Screenshot shows BitBucket Administration with Users selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/add-user.png)

4. Select **Create user**.

   ![Screenshot shows BitBucket Administration with Create user selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/create-user.png)

5. On the **Create User** dialog page, perform the following steps:

   ![Screenshot shows the Create user dialog box where you can perform these steps.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kantegassoforbitbucket-tutorial/details.png)


   a. In the **Username** textbox, type the email of user like Brittasimon@contoso.com.


   b. In the **Full Name** textbox, type full name of the user like Britta Simon.


   c. In the **Email address** textbox, type the email address of user like Brittasimon@contoso.com.


   d. In the **Password** textbox, type the password of user.


   e. In the **Confirm Password** textbox, reenter the password of user.


   f. Select **Create user**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Kantega SSO for Bitbucket Sign on URL where you can initiate the login flow.
- Go to Kantega SSO for Bitbucket Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Kantega SSO for Bitbucket for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Kantega SSO for Bitbucket tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Kantega SSO for Bitbucket for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Kantega SSO for Bitbucket you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
