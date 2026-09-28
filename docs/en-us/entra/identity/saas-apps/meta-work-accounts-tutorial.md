<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/meta-work-accounts-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Meta Work Accounts for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Meta Work Accounts with Microsoft Entra ID. When you integrate Meta Work Accounts with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Meta Work Accounts.
- Enable your users to be automatically signed-in to Meta Work Accounts with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Meta Work Accounts single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Meta Work Accounts supports **SP and IDP** initiated SSO.

## Add Meta Work Accounts from the gallery

To configure the integration of Meta Work Accounts into Microsoft Entra ID, you need to add Meta Work Accounts from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Meta Work Accounts** in the search box.
4. Select **Meta Work Accounts** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Meta Work Accounts

Configure and test Microsoft Entra SSO with Meta Work Accounts using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Meta Work Accounts.

To configure and test Microsoft Entra SSO with Meta Work Accounts, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Meta Work Accounts SSO](#configure-meta-work-accounts-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Meta Work Accounts test user](#create-meta-work-accounts-test-user)** - to have a counterpart of B.Simon in Meta Work Accounts that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Meta Work Accounts** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://work.facebook.com/company/<ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: ` https://work.facebook.com/work/saml.php?__cid=<ID>`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://work.facebook.com`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Engage the [Work Accounts team](https://www.workplace.com/help/work) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. On the **Set up Meta Work Accounts** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Meta Work Accounts SSO

1. Log in to your Meta Work Accounts company site as an administrator.
2. Go to **Security** > **Single Sign-On**.
3. Enable **Single-sign on\(SSO\)** checkbox and select **+Add new SSO Provider**.

1. On the **Single Sign-On \(SSO\) Setup** page, perform the following steps:

1. Enter a valid **Name of the SSO Provider**.
2. In the **SAML URL** textbox, paste the **Login URL** value which you copied previously.
3. In the **SAML Issuer URL** textbox, paste the **Microsoft Entra Identifier** value which you copied previously.
4. **Enable SAML logout redirection** checkbox and in the **SAML Logout URL** textbox, paste the **Logout URL** value which you copied previously.
5. Open the downloaded **Certificate \(Base64\)** into Notepad and paste the content into the **SAML Certificate** textbox.
6. Copy **Audience URL** value, paste this value into the **Identifier** textbox in the **Basic SAML Configuration** section.
7. Copy **ACS \(Assertion Consumer Service\) URL** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section.
8. In the **Test SSO Setup** section, enter a valid email in the textbox and select **Test SSO**.
9. Select **Save Changes**.

### Create Meta Work Accounts test user

In this section, you create a user called Britta Simon in Meta Work Accounts. Work with the [Work Accounts team](https://www.workplace.com/help/work) to add the users in the Meta Work Accounts platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Meta Work Accounts Sign on URL where you can initiate the login flow.
- Go to Meta Work Accounts Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Meta Work Accounts for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Meta Work Accounts tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Meta Work Accounts for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Meta Work Accounts you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
