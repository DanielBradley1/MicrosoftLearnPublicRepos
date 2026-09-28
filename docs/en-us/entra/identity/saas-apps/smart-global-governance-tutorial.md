<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/smart-global-governance-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Smart Global Governance for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Smart Global Governance with Microsoft Entra ID. When you integrate Smart Global Governance with Microsoft Entra ID, you can:

- Use Microsoft Entra ID to control who can access Smart Global Governance.
- Enable your users to be automatically signed in to Smart Global Governance with their Microsoft Entra accounts.
- Manage your accounts in one central location: the Azure portal.

To learn more about SaaS app integration with Microsoft Entra ID, see [Single sign-on to applications in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Smart Global Governance subscription with single sign-on \(SSO\) enabled.

## Article description

In this article, you configure and test Microsoft Entra SSO in a test environment.

Smart Global Governance supports SP-initiated and IDP-initiated SSO.

After you configure Smart Global Governance, you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session controls extend from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).

## Add Smart Global Governance from the gallery

To configure the integration of Smart Global Governance into Microsoft Entra ID, you need to add Smart Global Governance from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Smart Global Governance** in the search box.
4. Select **Smart Global Governance** in the results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Smart Global Governance

You'll configure and test Microsoft Entra SSO with Smart Global Governance by using a test user named B.Simon. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the corresponding user in Smart Global Governance.

To configure and test Microsoft Entra SSO with Smart Global Governance, you take these high-level steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** to enable your users to use the feature.

   1. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on.
   2. **[Grant access to the test user](#grant-access-to-the-test-user)** to enable the user to use Microsoft Entra single sign-on.

2. **[Configure Smart Global Governance SSO](#configure-smart-global-governance-sso)** on the application side.

   1. **[Create a Smart Global Governance test user](#create-a-smart-global-governance-test-user)** as a counterpart to the Microsoft Entra representation of the user.

3. **[Test SSO](#test-sso)** to verify that the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Azure portal:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Smart Global Governance** application integration page, in the **Manage** section, select **single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil button for **Basic SAML Configuration** to edit the settings:

   ![Pencil button for Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, if you want to configure the application in IDP-initiated mode, take the following steps.

   a. In the **Identifier** box, enter one of these URLs:

   - `https://eu-fr-south.console.smartglobalprivacy.com/platform/authentication-saml2/metadata`
   - `https://eu-fr-south.console.smartglobalprivacy.com/dpo/authentication-saml2/metadata`


   b. In the **Reply URL** box, enter one of these URLs:


   - `https://eu-fr-south.console.smartglobalprivacy.com/platform/authentication-saml2/acs`
   - `https://eu-fr-south.console.smartglobalprivacy.com/dpo/authentication-saml2/acs`

6. If you want to configure the application in SP-initiated mode, select **Set additional URLs** and complete the following step.

   - In the **Sign-on URL** box, enter one of these URLs:
   - `https://eu-fr-south.console.smartglobalprivacy.com/dpo`
   - `https://eu-fr-south.console.smartglobalprivacy.com/platform`

7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select the **Download** link for **Certificate \(Raw\)** to download the certificate and save it on your computer:

   ![Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

8. In the **Set up Smart Global Governance** section, copy the appropriate URL or URLs, based on your requirements:

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

### Grant access to the test user

In this section, you enable B.Simon to use single sign-on by granting that user access to Smart Global Governance.

1. Browse to **Entra ID** > **Enterprise apps**.
2. In the applications list, select **Smart Global Governance**.
3. In the app's overview page, in the **Manage** section, select **Users and groups**:

   ![Select Users and groups](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/users-groups-blade.png)

4. Select **Add user**, and then select **Users and groups** in the **Add Assignment** dialog box:

   ![Select Add user](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-assign-user.png)

5. In the **Users and groups** dialog box, select **B.Simon** in the **Users** list, and then select the **Select** button at the bottom of the screen.
6. If you're expecting any role value in the SAML assertion, in the **Select Role** dialog box, select the appropriate role for the user from the list and then select the **Select** button at the bottom of the screen.
7. In the **Add Assignment** dialog box, select **Assign**.

## Configure Smart Global Governance SSO

To configure single sign-on on the Smart Global Governance side, you need to send the downloaded raw certificate and the appropriate URLs that you copied from Azure portal to the [Smart Global Governance support team](mailto:support.tech@smartglobal.com). They configure the SAML SSO connection to be correct on both sides.

### Create a Smart Global Governance test user

Work with the [Smart Global Governance support team](mailto:support.tech@smartglobal.com) to add a user named B.Simon in Smart Global Governance. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra SSO configuration by using Access Panel.

When you select the Smart Global Governance tile in Access Panel, you should be automatically signed in to the Smart Global Governance instance for which you set up SSO. For more information about Access Panel, see [Introduction to Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [Tutorials on how to integrate SaaS apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [What is session control in Microsoft Defender for Cloud Apps?](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
- [How to protect Smart Global Governance with advanced visibility and controls](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
