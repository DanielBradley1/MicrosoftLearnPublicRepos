<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/instavr-viewer-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure InstaVR Viewer for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate InstaVR Viewer with Microsoft Entra ID. Integrating InstaVR Viewer with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to InstaVR Viewer.
- You can enable your users to be automatically signed-in to InstaVR Viewer \(Single Sign-On\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on). If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- InstaVR Viewer single sign-on enabled subscription

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- InstaVR Viewer supports **SP** initiated SSO
- InstaVR Viewer supports **Just In Time** user provisioning

## Adding InstaVR Viewer from the gallery

To configure the integration of InstaVR Viewer into Microsoft Entra ID, you need to add InstaVR Viewer from the gallery to your list of managed SaaS apps.

**To add InstaVR Viewer from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **InstaVR Viewer**, select **InstaVR Viewer** from result panel then select **Add** button to add the application.

   ![InstaVR Viewer in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with InstaVR Viewer based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in InstaVR Viewer needs to be established.

To configure and test Microsoft Entra single sign-on with InstaVR Viewer, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure InstaVR Viewer Single Sign-On](#configure-instavr-viewer-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create InstaVR Viewer test user](#create-instavr-viewer-test-user)** - to have a counterpart of Britta Simon in InstaVR Viewer that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with InstaVR Viewer, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **InstaVR Viewer** application integration page, select **Single sign-on**.

   ![Configure single sign-on link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   ![InstaVR Viewer Domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/sp-identifier.png)


   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://console.instavr.co/auth/saml/login/<WEBPackagedURL>`


   Note


   There's no fixed pattern for Sign on URL. It's generated when the InstaVR Viewer customer does web packaging. It's unique for every customer and package. For getting the exact Sign on URL you need to login to your InstaVR Viewer instance and do web packaging.


   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://console.instavr.co/auth/saml/sp/<WEBPackagedURL>`


   Note


   The Identifier value isn't real. Update this value with the actual Identifier value which is explained later in this article.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** and **Federation Metadata File** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadata-certificatebase64.png)

7. On the **Set up InstaVR Viewer** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)


   a. Login URL


   b. Microsoft Entra Identifier


   c. Logout URL

### Configure InstaVR Viewer Single Sign-On

1. Open a new web browser window and log into your InstaVR Viewer company site as an administrator.
2. Select **User Icon** and select **Account**.

   ![Screenshot shows your InstaVR Viewer site with a user selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/instavr-viewer-tutorial/tutorial-instavr-viewer-account.png)

3. Scroll down to the **SAML Auth** and perform the following steps:

   ![Screenshot shows the SAML Auth page where you can enter the values described in this step.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/instavr-viewer-tutorial/tutorial-instavr-viewer-configure.png)


   a. In the **SSO URL** textbox, paste the **Login URL** value, which you copied previously.


   b. In the **Logout URL** textbox, paste the **Logout URL** value, which you copied previously.


   c. In the **Entity ID** textbox, paste the **Microsoft Entra Identifier** value, which you copied previously.


   d. To upload your downloaded Certificate file, select **Update**.


   e. To upload your downloaded Federation Metadata file, select **Update**.


   f. Copy the **Entity ID** value and paste into the **Identifier \(Entity ID\)** text box on the **Basic SAML Configuration** section.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

### Create InstaVR Viewer test user

In this section, a user called Britta Simon is created in InstaVR Viewer. InstaVR Viewer supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in InstaVR Viewer, a new one is created after authentication. If you face any problems, please contact to [InstaVR Viewer support team](mailto:contact@instavr.co).

### Test single sign-on

1. Open a new web browser window and log into your InstaVR Viewer company site as an administrator.
2. Select **Package** from the left navigation panel and select **Make package for Web**.

   ![Screenshot shows InstaVR Viewer company site with Select Package and Make package for Web selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/instavr-viewer-tutorial/tutorial-instavr-viewer-testing1.png)

3. Select **Download**.

   ![Screenshot shows the Download icon selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/instavr-viewer-tutorial/tutorial-instavr-viewer-testing2.png)

4. Select **Open Hosted Page** after that it's redirected to Microsoft Entra ID for login.

   ![Screenshot shows Open Hosted Page selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/instavr-viewer-tutorial/tutorial-instavr-viewer-testing3.png)

5. Enter your Microsoft Entra credentials to successfully login to the Microsoft Entra ID via SSO.

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
