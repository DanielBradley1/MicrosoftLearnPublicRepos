<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/trisotechdigitalenterpriseserver-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Trisotech Digital Enterprise Server for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Trisotech Digital Enterprise Server with Microsoft Entra ID. Integrating Trisotech Digital Enterprise Server with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to Trisotech Digital Enterprise Server.
- You can enable your users to be automatically signed-in to Trisotech Digital Enterprise Server \(Single Sign-On\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on). If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Trisotech Digital Enterprise Server single sign-on enabled subscription

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Trisotech Digital Enterprise Server supports **SP** initiated SSO
- Trisotech Digital Enterprise Server supports **Just In Time** user provisioning

## Adding Trisotech Digital Enterprise Server from the gallery

To configure the integration of Trisotech Digital Enterprise Server into Microsoft Entra ID, you need to add Trisotech Digital Enterprise Server from the gallery to your list of managed SaaS apps.

**To add Trisotech Digital Enterprise Server from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **Trisotech Digital Enterprise Server**, select **Trisotech Digital Enterprise Server** from result panel then select **Add** button to add the application.

   ![Trisotech Digital Enterprise Server in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with Trisotech Digital Enterprise Server based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in Trisotech Digital Enterprise Server needs to be established.

To configure and test Microsoft Entra single sign-on with Trisotech Digital Enterprise Server, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure Trisotech Digital Enterprise Server Single Sign-On](#configure-trisotech-digital-enterprise-server-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create Trisotech Digital Enterprise Server test user](#create-trisotech-digital-enterprise-server-test-user)** - to have a counterpart of Britta Simon in Trisotech Digital Enterprise Server that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with Trisotech Digital Enterprise Server, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Trisotech Digital Enterprise Server** application integration page, select **Single sign-on**.

   ![Configure single sign-on link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   ![Trisotech Digital Enterprise Server Domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/sp-identifier.png)


   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://<companyname>.trisotech.com`


   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<companyname>.trisotech.com`


   Note


   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [Trisotech Digital Enterprise Server Client support team](mailto:support@trisotech.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Configure Trisotech Digital Enterprise Server Single Sign-On

1. In a different web browser window, sign in to your Trisotech Digital Enterprise Server Configuration company site as an administrator.
2. Select the **Menu icon** and then select **Administration**.

   ![Screenshot shows the Administration icon in Microsoft Digital Enterprise Server.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/trisotechdigitalenterpriseserver-tutorial/user1.png)

3. Select **User Provider**.

   ![Screenshot shows User Provider selected from the menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/trisotechdigitalenterpriseserver-tutorial/user2.png)

4. In the **User Provider Configurations** section, perform the following steps:

   ![Screenshot shows the User Provider Configurations where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/trisotechdigitalenterpriseserver-tutorial/user3.png)


   a. Select **Secured Assertion Markup Language 2 \(SAML 2\)** from the dropdown in the **Authentication Method**.


   b. In the **Metadata URL** textbox, paste the **App Federation Metadata Url** value, which you have copied form the Azure portal.


   c. In the **Application ID** textbox, enter the URL using the following pattern: `https://<companyname>.trisotech.com`.


   d. Select **Save**


   e. Enter the domain name in the **Allowed Domains \(empty means everyone\)** textbox, it automatically assigns licenses for users matching the Allowed Domains


   f. Select **Save**

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

### Create Trisotech Digital Enterprise Server test user

In this section, a user called Britta Simon is created in Trisotech Digital Enterprise Server. Trisotech Digital Enterprise Server supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Trisotech Digital Enterprise Server, a new one is created after authentication.

Note

If you need to create a user manually, contact [Trisotech Digital Enterprise Server support team](mailto:support@trisotech.com).

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Trisotech Digital Enterprise Server tile in the Access Panel, you should be automatically signed in to the Trisotech Digital Enterprise Server for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
