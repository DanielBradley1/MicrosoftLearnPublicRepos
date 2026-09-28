<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/hiretual-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure hireEZ-SSO for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate hireEZ-SSO with Microsoft Entra ID. When you integrate hireEZ-SSO with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to hireEZ-SSO.
- Enable your users to be automatically signed-in to hireEZ-SSO with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- hireEZ-SSO single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- hireEZ-SSO supports **SP and IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add hireEZ-SSO from the gallery

To configure the integration of hireEZ-SSO into Microsoft Entra ID, you need to add hireEZ-SSO from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **hireEZ-SSO** in the search box.
4. Select **hireEZ-SSO** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for hireEZ-SSO

Configure and test Microsoft Entra SSO with hireEZ-SSO using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in hireEZ-SSO.

To configure and test Microsoft Entra SSO with hireEZ-SSO, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure hireEZ-SSO](#configure-hireez-sso)** - to configure the single sign-on settings on application side.

   1. **[Create hireEZ-SSO test user](#create-hireez-sso-test-user)** - to have a counterpart of B.Simon in hireEZ-SSO that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **hireEZ-SSO** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following step:

   a. In the **Identifier** text box, type the URL: `https://app.hireez.com/`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://api.hireez.com/v1/users/saml/login/<teamId>`

   Note

   The Reply URL value isn't real. Update this value with the actual Reply URL. Contact [hireEZ-SSO Client support team](mailto:support@hiretual.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Select the **Properties** tab on the left menu bar, copy the value of **User access URL**,and save it on your computer.

   ![Screenshot shows the User access URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/hiretual-tutorial/access-url.png "SSO Configuration")

7. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

8. On the **Set up hireEZ-SSO** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Attributes")

### Create a Microsoft Entra test user

In this section, you create a test user called B.Simon.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. Select **New user** > **Create new user**, at the top of the screen.
4. In the **User** properties, follow these steps:

   1. In the **Display name** field, enter `B.Simon`.
   2. In the **User principal name** field, enter the username@companydomain.extension. For example, `B.Simon@contoso.com`.
   3. Select the **Show password** check box, and then write down the value that's displayed in the **Password** box.
   4. Select **Review + create**.

5. Select **Create**.

### Assign the Microsoft Entra test user

In this section, you enable B.Simon to use single sign-on by granting access to hireEZ-SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **hireEZ-SSO**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure hireEZ-SSO

1. Log in to your hireEZ-SSO company site as an administrator.
2. Go to **Security & Compliance** > **Single Sign-On**.
3. In the **SAML2.0 Authentication** page, perform the following steps:

   ![Screenshot shows the SSO Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/hiretual-tutorial/configuration.png "SSO Configuration")


   1. In the **SAML2.O SSO URL** textbox, paste the **Login URL** which you have copied from the Microsoft Entra admin center.
   2. In the **Identity Provider Issuer** textbox, paste the **Microsoft Entra Identifier** which you have copied from the Microsoft Entra admin center.
   3. Copy the content from the **Federation Metadata XML** file, which you have downloaded from the Microsoft Entra admin center and paste it in the **Certificate** textbox.
   4. Enable **Single Sign-On Connection Status** button.
   5. Test your Single Sign-On integration first and then enable **Admin SP-Initiated Single Sign-On** button.


   Note


   If your Single Sign-On configuration has any errors or you had trouble to login to hireEZ-SSO Web App/Extension after you connected Admin SP-Initiated Single Sign-On, please contact [hireEZ-SSO support team](mailto:support@hiretual.com).

### Create hireEZ-SSO test user

In this section, you create a user called Britta Simon in hireEZ-SSO. Work with [hireEZ-SSO support team](mailto:support@hiretual.com) to add the users in the hireEZ-SSO platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to hireEZ-SSO Sign-on URL where you can initiate the login flow.
- Go to hireEZ-SSO Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the hireEZ-SSO for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the hireEZ-SSO tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the hireEZ-SSO for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure hireEZ-SSO you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
