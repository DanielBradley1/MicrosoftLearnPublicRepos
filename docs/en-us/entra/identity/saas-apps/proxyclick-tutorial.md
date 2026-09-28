<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/proxyclick-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Proxyclick for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Proxyclick with Microsoft Entra ID. When you integrate Proxyclick with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Proxyclick.
- Enable your users to be automatically signed-in to Proxyclick with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Proxyclick single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Proxyclick supports SP-initiated and IdP-initiated SSO.
- Proxyclick supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/proxyclick-provisioning-tutorial).

## Add Proxyclick from the gallery

To configure the integration of Proxyclick into Microsoft Entra ID, you need to add Proxyclick from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Proxyclick** in the search box.
4. Select **Proxyclick** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Proxyclick

Configure and test Microsoft Entra SSO with Proxyclick using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Proxyclick.

To configure and test Microsoft Entra SSO with Proxyclick, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Proxyclick SSO](#configure-proxyclick-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Proxyclick test user](#create-proxyclick-test-user)** - to have a counterpart of B.Simon in Proxyclick that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Proxyclick** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** dialog box, if you want to configure the application in IdP-initiated mode, perform the following steps.

   a. In the **Identifier** box, type a URL using the following pattern: `https://saml.proxyclick.com/init/<COMPANY_ID>`

   b. In the **Reply URL** box, type a URL using the following pattern: `https://saml.proxyclick.com/consume/<COMPANY_ID>`
6. If you want to configure the application in SP-initiated mode, select **Set additional URLs**. In the **Sign on URL** textbox, type a URL using the following pattern:

   `https://saml.proxyclick.com/init/<COMPANY_ID>`

   Note

   These values are placeholders. You need to use the actual Identifier,Reply URL and Sign on URL. Steps for getting these values are described later in this article.
7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select the **Download** link next to **Certificate \(Base64\)**, per your requirements, and save the certificate on your computer:

   ![Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. In the **Set up Proxyclick** section, copy the appropriate URLs, based on your requirements:

   ![Copy the configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Proxyclick SSO

1. In a new web browser window, sign in to your Proxyclick company site as an admin.
2. Select **Account & Settings**.

   ![Select Account & Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-tutorial/account.png)

3. Scroll down to the **Integrations** section and select **SAML**.

   ![Select SAML.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-tutorial/settings.png)

4. In the **SAML** section, take the following steps.

   ![SAML section](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-tutorial/configuration.png)


   1. Copy the **SAML Consumer URL** value and paste it into the **Reply URL** box in the **Basic SAML Configuration** dialog box.
   2. Copy the **SAML SSO Redirect URL** value and paste it into the **Sign on URL** and **Identifier** boxes in the **Basic SAML Configuration** dialog box.
   3. In the **SAML Request Method** list, select **HTTP Redirect**.
   4. In the **Issuer** box, paste the **Microsoft Entra Identifier** value that you copied.
   5. In the **SAML 2.0 Endpoint URL** box, paste the **Login URL** value that you copied.
   6. In Notepad, open the certificate file that you downloaded. Paste the contents of this file into the **Certificate** box.
   7. Select **Save Changes**.

### Create Proxyclick test user

To enable Microsoft Entra users to sign in to Proxyclick, you need to add them to Proxyclick. You need to add them manually.

To create a user account, take these steps:

1. Sign in to your Proxyclick company site as an admin.
2. Select **Colleagues** at the top of the window.

   ![Select Colleagues.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-tutorial/user.png)

3. Select **Add Colleague**.

   ![Select Add Colleague.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-tutorial/add-user.png)

4. In the **Add a colleague** section, take the following steps.

   ![Add a colleague section.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-tutorial/create-user.png)


   1. In the **Email** box, enter the email address of the user. In this case, **brittasimon@contoso.com**.
   2. In the **First Name** box, enter the first name of the user. In this case, **Britta**.
   3. In the **Last Name** box, enter the last name of the user. In this case, **Simon**.
   4. Select **Add User**.

Note

Proxyclick also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/proxyclick-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Proxyclick Sign on URL where you can initiate the login flow.
- Go to Proxyclick Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Proxyclick for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Proxyclick tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Proxyclick for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Proxyclick you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
