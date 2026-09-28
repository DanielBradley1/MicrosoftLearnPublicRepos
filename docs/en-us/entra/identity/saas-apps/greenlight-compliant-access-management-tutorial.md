<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/greenlight-compliant-access-management-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Greenlight Compliant Access Management for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Greenlight Compliant Access Management with Microsoft Entra ID. When you integrate Greenlight Compliant Access Management with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Greenlight Compliant Access Management.
- Enable your users to be automatically signed-in to Greenlight Compliant Access Management with their Microsoft Entra accounts.
- Manage your accounts in one central location.

To learn more about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Greenlight Compliant Access Management single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Greenlight Compliant Access Management supports **SP and IDP** initiated SSO
- Once you configure Greenlight Compliant Access Management you can enforce session control, which protect exfiltration and infiltration of your organization’s sensitive data in real-time. Session control extend from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).

## Adding Greenlight Compliant Access Management from the gallery

To configure the integration of Greenlight Compliant Access Management into Microsoft Entra ID, you need to add Greenlight Compliant Access Management from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Greenlight Compliant Access Management** in the search box.
4. Select **Greenlight Compliant Access Management** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra single sign-on for Greenlight Compliant Access Management

Configure and test Microsoft Entra SSO with Greenlight Compliant Access Management using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Greenlight Compliant Access Management.

To configure and test Microsoft Entra SSO with Greenlight Compliant Access Management, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   - **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   - **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Greenlight Compliant Access Management SSO](#configure-greenlight-compliant-access-management-sso)** - to configure the single sign-on settings on application side.

   - **[Create Greenlight Compliant Access Management test user](#create-greenlight-compliant-access-management-test-user)** - to have a counterpart of B.Simon in Greenlight Compliant Access Management that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Greenlight Compliant Access Management** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<CUSTOMER>.greenlightcorp.com/ebcpresq/checkLoginSAML.do`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<CUSTOMER>.greenlightcorp.com/ebcpresq/checkLoginSAML.do`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<CUSTOMER>.greenlightcorp.com/ebcpresq/checkLoginSAML.do`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Greenlight Compliant Access Management Client support team](mailto:support@greenlightcorp.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up Greenlight Compliant Access Management** section, copy the appropriate URL\(s\) based on your requirement.

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

In this section, you enable B.Simon to use single sign-on by granting access to Greenlight Compliant Access Management.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Greenlight Compliant Access Management**.
3. In the app's overview page, find the **Manage** section and select **Users and groups**.

   ![The "Users and groups" link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/users-groups-blade.png)

4. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.

   ![The Add User link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-assign-user.png)

5. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
6. If you're expecting any role value in the SAML assertion, in the **Select Role** dialog, select the appropriate role for the user from the list and then select the **Select** button at the bottom of the screen.
7. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Greenlight Compliant Access Management SSO

To configure single sign-on on **Greenlight Compliant Access Management** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Greenlight Compliant Access Management support team](mailto:support@greenlightcorp.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Greenlight Compliant Access Management test user

In this section, you create a user called B.Simon in Greenlight Compliant Access Management. Work with [Greenlight Compliant Access Management support team](mailto:support@greenlightcorp.com) to add the users in the Greenlight Compliant Access Management platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Greenlight Compliant Access Management tile in the Access Panel, you should be automatically signed in to the Greenlight Compliant Access Management for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [What is session control in Microsoft Defender for Cloud Apps?](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
- [How to protect Greenlight Compliant Access Management with advanced visibility and controls](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
