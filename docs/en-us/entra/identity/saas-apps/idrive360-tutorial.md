<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/idrive360-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure IDrive360 for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate IDrive360 with Microsoft Entra ID. When you integrate IDrive360 with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to IDrive360.
- Enable your users to be automatically signed-in to IDrive360 with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- IDrive360 single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- IDrive360 supports **SP and IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add IDrive360 from the gallery

To configure the integration of IDrive360 into Microsoft Entra ID, you need to add IDrive360 from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **IDrive360** in the search box.
4. Select **IDrive360** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for IDrive360

Configure and test Microsoft Entra SSO with IDrive360 using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in IDrive360.

To configure and test Microsoft Entra SSO with IDrive360, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure IDrive360 SSO](#configure-idrive360-sso)** - to configure the single sign-on settings on application side.

   1. **[Create IDrive360 test user](#create-idrive360-test-user)** - to have a counterpart of B.Simon in IDrive360 that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **IDrive360** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://www.idrive360.com/enterprise/sso`
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(PEM\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificate-base64-download.png)

8. On the **Set up IDrive360** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure IDrive360 SSO

1. Log in to your IDrive360 company site as an administrator.
2. Go to **Settings** > **Single Sign-on\(SSO\)** and perform the following steps.

   ![Single Sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/idrive360-tutorial/settings.png "Single Sign-on")


   a. In the **SSO Name** textbox, type a valid name.


   b. In the **Issuer URL** textbox, paste the **Microsoft Entra Identifier** value which you copied previously.


   c. In the **SSO Endpoint** textbox, paste the **Login URL** value which you copied previously.


   d. Select **Upload Certificate** to upload the **Certificate \(PEM\)**, which you have downloaded previously.


   e. Select **Configure Single Sign-On**.

### Create IDrive360 test user

1. In a different web browser window, sign in to your IDrive360 company site as an administrator
2. Navigate to the **Users** tab and select **Add User**.

   ![Users](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/idrive360-tutorial/add-user.png "Users")

3. In the **Create new user\(s\)** section, perform the following steps.

   ![Create Users](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/idrive360-tutorial/new-user.png "Create Users")


   a. Enter valid **Email Address** in the **Email** textbox.


   b. Select **Create**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to IDrive360 Sign on URL where you can initiate the login flow.
- Go to IDrive360 Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the IDrive360 for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the IDrive360 tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the IDrive360 for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure IDrive360 you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
