<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/rhombus-systems-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Rhombus Systems for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Rhombus Systems with Microsoft Entra ID. When you integrate Rhombus Systems with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Rhombus Systems.
- Enable your users to be automatically signed-in to Rhombus Systems with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Rhombus Systems single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Rhombus Systems supports **SP and IDP** initiated SSO.
- Rhombus Systems supports **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Rhombus Systems from the gallery

To configure the integration of Rhombus Systems into Microsoft Entra ID, you need to add Rhombus Systems from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Rhombus Systems** in the search box.
4. Select **Rhombus Systems** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Rhombus Systems

Configure and test Microsoft Entra SSO with Rhombus Systems using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Rhombus Systems.

To configure and test Microsoft Entra SSO with Rhombus Systems, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Rhombus Systems SSO](#configure-rhombus-systems-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Rhombus Systems test user](#create-rhombus-systems-test-user)** - to have a counterpart of B.Simon in Rhombus Systems that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Rhombus Systems** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you have **Service Provider metadata file** and wish to configure in **IDP** initiated mode, perform the following steps:

   a. Select **Upload metadata file**.

   ![Upload metadata file](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/upload-metadata.png)


   b. Select **folder logo** to select the metadata file and select **Upload**.


   ![choose metadata file](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/browse-upload-metadata.png)


   c. After the metadata file is successfully uploaded, the **Identifier** and **Reply URL** values get auto populated in Basic SAML Configuration section.


   Note


   If the **Identifier** and **Reply URL** values don't get auto populated, then fill in the values manually according to your requirement.

6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://console.rhombussystems.com/login/`
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up Rhombus Systems** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Rhombus Systems SSO

1. Log in to your Rhombus Systems company site as an administrator.
2. Go to **Settings** icon and select **Single Sign-On**.
3. On the **Single Sign-On** page, perform the following steps.

   ![Screenshot shows settings of SSO configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rhombus-systems-tutorial/settings.png "Account")


   1. Enable **Use Single Sign-On** button.
   2. Enable **Just-In-Time User Creation** button.
   3. Enter a valid **Team name** in the textbox.
   4. **Select Users** from the dropdown in the **SSO Recovery Users**.
   5. Download **SP Metadata** file and upload the metadata file into the **Basic SAML Configuration** section.
   6. Copy **Federation Metadata XML** into Notepad and paste the content into the **IDP MetaData XML** textbox.
   7. Select **Save**.

### Create Rhombus Systems test user

In this section, a user called Britta Simon is created in Rhombus Systems. Rhombus Systems supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Rhombus Systems, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Rhombus Systems Sign on URL where you can initiate the login flow.
- Go to Rhombus Systems Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Rhombus Systems for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Rhombus Systems tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Rhombus Systems for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Rhombus Systems you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
