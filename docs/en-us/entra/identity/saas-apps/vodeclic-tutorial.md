<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/vodeclic-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Vodeclic for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Vodeclic with Microsoft Entra ID. Integrating Vodeclic with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to Vodeclic.
- You can enable your users to be automatically signed-in to Vodeclic \(Single Sign-On\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on). If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Vodeclic single sign-on enabled subscription

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Vodeclic supports **SP** and **IDP** initiated SSO

## Adding Vodeclic from the gallery

To configure the integration of Vodeclic into Microsoft Entra ID, you need to add Vodeclic from the gallery to your list of managed SaaS apps.

**To add Vodeclic from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **Vodeclic**, select **Vodeclic** from result panel then select **Add** button to add the application.

   ![Vodeclic in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with Vodeclic based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in Vodeclic needs to be established.

To configure and test Microsoft Entra single sign-on with Vodeclic, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure Vodeclic Single Sign-On](#configure-vodeclic-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create Vodeclic test user](#create-vodeclic-test-user)** - to have a counterpart of Britta Simon in Vodeclic that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with Vodeclic, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Vodeclic** application integration page, select **Single sign-on**.

   ![Configure single sign-on link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

   ![Screenshot shows the Basic SAML Configuration, where you can enter Identifier, Reply U R L, and select Save.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/idp-intiated.png)


   a. In the **Identifier** text box, type a URL using the following pattern: `https://<companyname>.lms.vodeclic.net/auth/saml`


   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<companyname>.lms.vodeclic.net/auth/saml/callback`

6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   ![Screenshot shows Set additional U R Ls where you can enter a Sign on U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadata-upload-additional-signon.png)


   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<companyname>.lms.vodeclic.net/auth/saml`


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Vodeclic Client support team](mailto:hotline@vodeclic.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up Vodeclic** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)


   a. Login URL


   b. Microsoft Entra Identifier


   c. Logout URL

### Configure Vodeclic Single Sign-On

To configure single sign-on on **Vodeclic** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Vodeclic support team](mailto:hotline@vodeclic.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

### Create Vodeclic test user

In this section, you create a user called Britta Simon in Vodeclic. Work with [Vodeclic support team](mailto:hotline@vodeclic.com) to add the users in the Vodeclic platform. Users must be created and activated before you use single sign-on.

Note

According to application requirements, you might need to get your machine added to an allow list. For that to happen, you need to share your public IP address with the [Vodeclic support team](mailto:hotline@vodeclic.com).

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Vodeclic tile in the Access Panel, you should be automatically signed in to the Vodeclic for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
