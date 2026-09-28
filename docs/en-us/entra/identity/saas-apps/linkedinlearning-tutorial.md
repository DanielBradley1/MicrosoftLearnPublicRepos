<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/linkedinlearning-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure LinkedIn Learning for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate LinkedIn Learning with Microsoft Entra ID. When you integrate LinkedIn Learning with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to LinkedIn Learning.
- Enable your users to be automatically signed-in to LinkedIn Learning with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- LinkedIn Learning single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- LinkedIn Learning supports **SP and IDP** initiated SSO.
- LinkedIn Learning supports **Just In Time** user provisioning.

## Add LinkedIn Learning from the gallery

To configure the integration of LinkedIn Learning into Microsoft Entra ID, you need to add LinkedIn Learning from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **LinkedIn Learning** in the search box.
4. Select **LinkedIn Learning** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for LinkedIn Learning

Configure and test Microsoft Entra SSO with LinkedIn Learning using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in LinkedIn Learning.

To configure and test Microsoft Entra SSO with LinkedIn Learning, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure LinkedIn Learning SSO](#configure-linkedin-learning-sso)** - to configure the single sign-on settings on application side.

   1. **[Assign Licenses](#assign-licenses)**- to have a counterpart of B.Simon in LinkedIn Learning that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **LinkedIn Learning** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

   a. In the **Identifier** textbox, enter the **Entity ID** copied from LinkedIn Portal.

   b. In the **Reply URL** textbox, enter the **Assertion Consumer Service \(ACS\) Url** copied from LinkedIn Portal.

   c. If you wish to configure the application in **SP Initiated** mode then select **Set additional URLs** option in the **Basic SAML Configuration** section where you specify your sign-on URL. To create your login URL copy the **Assertion Consumer Service \(ACS\) Url** and replace /saml/ with /login/. Once that has been done, the sign-on URL should have the following pattern:

   `https://www.linkedin.com/checkpoint/enterprise/login/<AccountId>?application=learning&applicationInstanceId=<InstanceId>`

   Note

   These values aren't real. You update these values with the actual Identifier, Reply URL and Sign on URL which is explained later in the **Configure LinkedIn Learning SSO** section of article.
6. LinkedIn Learning application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes, whereas **nameidentifier** is mapped with **user.userprincipalname**. LinkedIn Learning application expects **nameidentifier** to be mapped with **user.mail**, so you need to edit the attribute mapping by selecting **Edit** icon and change the attribute mapping.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png)

7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up LinkedIn Learning** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure LinkedIn Learning SSO

1. Log in to your LinkedIn Learning company site as an administrator.
2. Select **Go to Admin** > **Me** > **Authenticate**.

   ![Account](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/welcome-back-authenticate.png "Account")

3. Select **Configure single sign-on** under **Authenticate** and select **Add new SSO**.

   ![Configure single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/admin.png "Configure single sign-on")

4. Select **SAML** from the **Add new SSO** dropdown.

   ![SAML Authentication](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/new-method.png "SAML Authentication")

5. Under **Basics** tab, enter **SAML Connection Name** and select **Next**.

   ![SSO Connection](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/users.png "SSO Connection")

6. Navigate to **Identity provider settings** tab, select **Download file** to download the metadata file and save it on your computer and select **Next**.

   ![Identity provider settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/download-file.png "Identity provider settings")


   Note


   You may not be able to import this file into your Identity Provider. For example, Okta doesn't have this functionality. If this case matches your configuration requirements, continue to Working with Individual Fields.

7. In the **Identity provider settings** tab, select **Load and copy information from fields** to copy the required fields and paste into the **Basic SAML Configuration** section and select **Next**.

   ![Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/fields.png "Settings")

8. Navigate to **SSO settings** tab, select **Upload XML file** to upload the **Federation Metadata XML** file which you have downloaded.

   ![Certificate file](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/upload-file.png "Certificate file")

9. Fill the required fields manually which you have copied under **SSO settings** tab.

   ![Entering Values](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/certificate.png "Entering Values")

10. Under **SSO settings**, select your SSO options as per your requirement and select **Save**.

    ![SSO settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/options.png "SSO settings")

#### Enabling Single Sign-On

After completing your configuration, enable SSO by selecting **Active** from the SSO Status drop down.

![Enabling Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/configuration.png "Enabling Single Sign-On")

### Assign licenses

Once you have enabled SSO, you can automatically assign licenses to your employees by toggling **Automatically provision licenses** to **On** and select **Save**. When you enable this option, users are automatically granted a license when they are authenticated for the first time.

![Assign Licenses](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinlearning-tutorial/license.png "Assign Licenses")

Note

If you don't enable this option, an admin must add users manually in the People tab. LinkedIn Learning identifies users by their email address.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to LinkedIn Learning Sign on URL where you can initiate the login flow.
- Go to LinkedIn Learning Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the LinkedIn Learning for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the LinkedIn Learning tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the LinkedIn Learning for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure LinkedIn Learning you can enforce Session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
