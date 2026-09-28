<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/uberflip-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Uberflip for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Uberflip with Microsoft Entra ID.

Integrating Uberflip with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to Uberflip.
- You can enable your users to be automatically signed in to Uberflip \(single sign-on\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location: the Azure portal.

For details about software as a service \(SaaS\) app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

To configure Microsoft Entra integration with Uberflip, you need the following items:

- A Microsoft Entra subscription. If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.
- An Uberflip subscription with single sign-on enabled.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

Uberflip supports the following features:

- SP-initiated and IDP-initiated single sign-on \(SSO\).
- Just-in-time user provisioning.

## Add Uberflip from the Azure Marketplace

To configure the integration of Uberflip into Microsoft Entra ID, you need to add Uberflip from the Azure Marketplace to your list of managed SaaS apps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.

   ![The New application option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-new-app.png)

3. In the search box, enter **Uberflip**. In the search results, select **Uberflip**, and then select **Add** to add the application.

   ![Uberflip in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with Uberflip based on a test user named **B Simon**. For single sign-on to work, you need to establish a link between a Microsoft Entra user and a related user in Uberflip.

To configure and test Microsoft Entra single sign-on with Uberflip, you need to complete the following building blocks:

1. **[Configure Microsoft Entra single sign-on](#configure-azure-ad-single-sign-on)** to enable your users to use this feature.
2. **[Configure Uberflip single sign-on](#configure-uberflip-single-sign-on)** to configure the single sign-on settings on the application side.
3. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with B. Simon.
4. **Assign the Microsoft Entra test user** to enable B. Simon to use Microsoft Entra single sign-on.
5. **[Create an Uberflip test user](#create-an-uberflip-test-user)** so that there's a user named B. Simon in Uberflip who's linked to the Microsoft Entra user named B. Simon.
6. **[Test single sign-on](#test-single-sign-on)** to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with Uberflip, take the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Uberflip** application integration page, select **Single sign-on**.

   ![Configure single sign-on option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. In the **Select a single sign-on method** pane, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** pane, select **Edit** \(the pencil icon\) to open the **Basic SAML Configuration** pane.

   ![Screenshot shows the Basic SAML Configuration, where you can enter a Reply U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** pane, do one of the following steps, depending on which SSO mode you want to configure:

   - To configure the application in IDP-initiated SSO mode, in the **Reply URL \(Assertion Consumer Service URL\)** box, enter a URL by using the following pattern:

     `https://app.uberflip.com/sso/saml2/<IDPID>/<ACCOUNTID>`

     ![Uberflip domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/both-replyurl.png)


     Note


     This value isn't real. Update this value with the actual reply URL. To get the actual value, contact the [Uberflip support team](mailto:support@uberflip.com). You can also refer to the patterns shown in the **Basic SAML Configuration** pane.

   - To configure the application in SP-initiated SSO mode, select **Set additional URLs**, and in the **Sign-on URL** box, enter this URL:

     `https://app.uberflip.com/users/login`

     ![Screenshot shows Set additional U R Ls where you can enter a Sign on U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/both-signonurl.png)

6. On the **Set up Single Sign-On with SAML** pane, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options and save it on your computer.

   ![The Federation Metadata XML download option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. In the **Set up Uberflip** pane, copy the URL or URLs that you need:

   - **Login URL**
   - **Microsoft Entra Identifier**
   - **Logout URL**


   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Configure Uberflip single sign-on

To configure single sign-on on the Uberflip side, you need to send the downloaded Federation Metadata XML and the appropriate copied URLs to the [Uberflip support team](mailto:support@uberflip.com). The Uberflip team will make sure the SAML SSO connection is set properly on both sides.

### Create a Microsoft Entra test user

In this section, you create a test user named B. Simon.

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

In this section, you enable B. Simon to use Azure single sign-on by granting their access to Uberflip.

1. Browse to **Entra ID** > **Enterprise apps** > **Uberflip**.

   ![Enterprise applications pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

2. In the applications list, select **Uberflip**.

   ![Uberflip in the applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

3. In the left pane, under **MANAGE**, select **Users and groups**.

   ![The "Users and groups" option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/users-groups-blade.png)

4. Select **+ Add user**, and then select **Users and groups** in the **Add Assignment** pane.

   ![The Add Assignment pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-assign-user.png)

5. In the **Users and groups** pane, select **B Simon** in the **Users** list, and then choose **Select** at the bottom of the pane.
6. If you're expecting a role value in the SAML assertion, then in the **Select Role** pane, select the appropriate role for the user from the list. At the bottom of the pane, choose **Select**.
7. In the **Add Assignment** pane, select **Assign**.

### Create an Uberflip test user

A user named B. Simon is now created in Uberflip. You don't have to do anything to create this user. Uberflip supports just-in-time user provisioning, which is enabled by default. If a user named B. Simon doesn't already exist in Uberflip, a new one is created after authentication.

Note

If you need to create a user manually, contact the [Uberflip support team](mailto:support@uberflip.com).

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration by using the My Apps portal.

When you select **Uberflip** in the My Apps portal, you should be automatically signed in to the Uberflip subscription for which you set up single sign-on. For more information about the My Apps portal, see [Access and use apps on the My Apps portal](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles for integrating SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
