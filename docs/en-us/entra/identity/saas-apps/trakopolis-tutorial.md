<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/trakopolis-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Trakopolis for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Trakopolis with Microsoft Entra ID. Integrating Trakopolis with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to Trakopolis.
- You can enable your users to be automatically signed-in to Trakopolis \(Single Sign-On\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on). If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Trakopolis single sign-on enabled subscription

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Trakopolis supports **SP** initiated SSO

## Adding Trakopolis from the gallery

To configure the integration of Trakopolis into Microsoft Entra ID, you need to add Trakopolis from the gallery to your list of managed SaaS apps.

**To add Trakopolis from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **Trakopolis**, select **Trakopolis** from result panel then select **Add** button to add the application.

   ![Trakopolis in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with Trakopolis based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in Trakopolis needs to be established.

To configure and test Microsoft Entra single sign-on with Trakopolis, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure Trakopolis Single Sign-On](#configure-trakopolis-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create Trakopolis test user](#create-trakopolis-test-user)** - to have a counterpart of Britta Simon in Trakopolis that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with Trakopolis, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Trakopolis** application integration page, select **Single sign-on**.

   ![Configure single sign-on link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   ![Trakopolis Domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/sp-identifier.png)


   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://<company name>.trakopolis.com/`


   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<company name>.trakopolis.com`


   Note


   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [Trakopolis Client support team](mailto:support@cantelematics.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Trakopolis** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)


   a. Login URL


   b. Microsoft Entra Identifier


   c. Logout URL

### Configure Trakopolis Single Sign-On

To configure single sign-on on **Trakopolis** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Trakopolis support team](mailto:support@cantelematics.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

### Create Trakopolis test user

In this section, you create a user called Britta Simon in Trakopolis. Work with [Trakopolis support team](mailto:support@cantelematics.com) to add the users in the Trakopolis platform. Users must be created and activated before you use single sign-on.

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Trakopolis tile in the Access Panel, you should be automatically signed in to the Trakopolis for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
