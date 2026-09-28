<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/happyfox-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure HappyFox for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate HappyFox with Microsoft Entra ID. When you integrate HappyFox with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to HappyFox.
- Enable your users to be automatically signed-in to HappyFox with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- HappyFox single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- HappyFox supports **SP** initiated SSO.
- HappyFox supports **Just In Time** user provisioning.

## Add HappyFox from the gallery

To configure the integration of HappyFox into Microsoft Entra ID, you need to add HappyFox from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **HappyFox** in the search box.
4. Select **HappyFox** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for HappyFox

Configure and test Microsoft Entra SSO with HappyFox using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in HappyFox.

To configure and test Microsoft Entra SSO with HappyFox, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure HappyFox SSO](#configure-happyfox-sso)** - to configure the single sign-on settings on application side.

   1. **[Create HappyFox test user](#create-happyfox-test-user)** - to have a counterpart of B.Simon in HappyFox that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **HappyFox** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.happyfox.com/`

   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.happyfox.com/saml/metadata/`

   Note

   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [HappyFox Client support team](https://support.happyfox.com/home) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up HappyFox** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

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

In this section, you enable B.Simon to use single sign-on by granting access to HappyFox.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **HappyFox**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure HappyFox SSO

1. In a different web browser window, sign-on to your HappyFox tenant as an administrator.
2. Navigate to **Manage**, select **Integrations** tab.

   ![Screenshot that shows the "Manage" page with the "Integrations" tab selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/happyfox-tutorial/header.png)

3. In the Integrations tab, select **Configure** under **SAML Integration** to open the Single Sign On Settings.

   ![Screenshot that shows the "S A M L Integration" setting with the "configure" action selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/happyfox-tutorial/configure.png)

4. In the **SAML Configuration** section, in the **SSO Target URL** textbox, paste the **Login URL** value from the **Set up HappyFox** section.
5. Open the certificate downloaded from Azure portal in notepad and paste its content in **IdP Signature** section.

   ![Screenshot that shows the "I d P Signature" section highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/happyfox-tutorial/certificate.png)

6. Select **Save Settings** button.

   ![Configure Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/happyfox-tutorial/save-settings.png)

### Create HappyFox test user

In this section, a user called Britta Simon is created in HappyFox. HappyFox supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in HappyFox, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the My Apps.

1. When you select the HappyFox tile in the My Apps, you should get login page of HappyFox application. You should see the **‘SAML’** button on the sign-in page.

   ![Plugin](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/happyfox-tutorial/apps.png)

2. Select the **SAML** button to log in to HappyFox using your Microsoft Entra account.

For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure HappyFox you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
