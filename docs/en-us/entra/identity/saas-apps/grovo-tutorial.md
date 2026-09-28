<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/grovo-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Grovo for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Grovo with Microsoft Entra ID. When you integrate Grovo with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Grovo.
- Enable your users to be automatically signed-in to Grovo with their Microsoft Entra accounts.
- Manage your accounts in one central location.

To learn more about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Grovo single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Grovo supports **SP and IDP** initiated SSO
- Grovo supports **Just In Time** user provisioning

## Adding Grovo from the gallery

To configure the integration of Grovo into Microsoft Entra ID, you need to add Grovo from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Grovo** in the search box.
4. Select **Grovo** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra single sign-on for Grovo

Configure and test Microsoft Entra SSO with Grovo using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Grovo.

To configure and test Microsoft Entra SSO with Grovo, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Grovo SSO](#configure-grovo-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Grovo test user](#create-grovo-test-user)** - to have a counterpart of B.Simon in Grovo that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Grovo** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<subdomain>.grovo.com/sso/saml2/metadata`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<subdomain>.grovo.com/sso/saml2/saml-assertion`

   c. Select **Set additional URLs**.

   d. In the **Relay State** text box, type a URL using the following pattern: `https://<subdomain>.grovo.com`
6. Select **Set additional URLs** and perform the following steps if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<subdomain>.grovo.com/sso/saml2/saml-assertion`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL, Sign-on URL and Relay State. Contact Grovo Client support team to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. On the **Set up Grovo** section, copy the appropriate URL\(s\) based on your requirement.

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

In this section, you enable B.Simon to use single sign-on by granting access to Grovo.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Grovo**.
3. In the app's overview page, find the **Manage** section and select **Users and groups**.

   ![The "Users and groups" link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/users-groups-blade.png)

4. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.

   ![The Add User link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-assign-user.png)

5. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
6. If you're expecting any role value in the SAML assertion, in the **Select Role** dialog, select the appropriate role for the user from the list and then select the **Select** button at the bottom of the screen.
7. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Grovo SSO

1. In a different web browser window, sign in to Grovo as Administrator.
2. Go to **Admin** > **Integrations**.

   ![Screenshot that shows the "Admin" menu with "Integrations" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/grovo-tutorial/tutorial_grovo_admin.png)

3. Select **SET UP** under **SP Initiated SAML 2.0** section.

   ![Screenshot that shows the "S P initiated S A M L 2.0" section with the "Set up" button selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/grovo-tutorial/tutorial_grovo_setup.png)

4. In the **SP Initiated SAML 2.0** pop-up window, perform the following steps:

   ![Grovo Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/grovo-tutorial/tutorial_grovo_saml.png)


   a. In the **Entity ID** textbox, paste the value of **Microsoft Entra Identifier**.


   b. In the **Single sign-on service endpoint** textbox, paste the value of **Login URL**.


   c. Select **Single sign-on service endpoint binding** as `urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect`.


   d. Open the downloaded **Base64 encoded certificate** from Azure portal in notepad, paste it into the **Public key** textbox.


   e. Select **Next**.

### Create Grovo test user

In this section, a user called B.Simon is created in Grovo. Grovo supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Grovo, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Grovo tile in the Access Panel, you should be automatically signed in to the Grovo for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
