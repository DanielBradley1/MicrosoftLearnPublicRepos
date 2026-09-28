<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/ideascale-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure IdeaScale for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate IdeaScale with Microsoft Entra ID. Integrating IdeaScale with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to IdeaScale.
- You can enable your users to be automatically signed-in to IdeaScale \(Single Sign-On\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on). If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- IdeaScale single sign-on enabled subscription

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- IdeaScale supports **SP** initiated SSO

## Adding IdeaScale from the gallery

To configure the integration of IdeaScale into Microsoft Entra ID, you need to add IdeaScale from the gallery to your list of managed SaaS apps.

**To add IdeaScale from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **IdeaScale**, select **IdeaScale** from result panel then select **Add** button to add the application.

   ![IdeaScale in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with IdeaScale based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in IdeaScale needs to be established.

To configure and test Microsoft Entra single sign-on with IdeaScale, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure IdeaScale Single Sign-On](#configure-ideascale-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create IdeaScale test user](#create-ideascale-test-user)** - to have a counterpart of Britta Simon in IdeaScale that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with IdeaScale, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **IdeaScale** application integration page, select **Single sign-on**.

   ![Configure single sign-on link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   ![IdeaScale Domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/sp-identifier.png)


   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://<companyname>.ideascale.com`


   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern:


   ```http
   http://<companyname>.ideascale.com
   https://<companyname>.ideascale.com
   ```


   Note


   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [IdeaScale Client support team](https://support.ideascale.com/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up IdeaScale** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)


   a. Login URL


   b. Microsoft Entra Identifier


   c. Logout URL

### Configure IdeaScale Single Sign-On

1. In a different web browser window, log in to your IdeaScale company site as an administrator.
2. Go to **Community Settings**.

   ![Community Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790847.png "Community Settings")

3. Go to **Security** > **Single Signon Settings**.

   ![Screenshot shows Single Signon Settings selected from the Security menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790848.png "Single Signon Settings")

4. As **Single-Signon Type**, select **SAML 2.0**.

   ![Single Signon Type](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790849.png "Single Signon Type")

5. On the **Single Signon Settings** dialog, perform the following steps:

   ![Screenshot shows the Single Signon Settings dialog box.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790850.png "Single Signon Settings")


   a. In **SAML IdP Entity ID** textbox, paste the value of **Microsoft Entra Identifier**..


   b. Open the downloaded metadata file from Azure portal into Notepad, copy the content of it and paste into the **SAML IdP Metadata** textbox.


   c. In **Logout Success URL** textbox, paste the value of **Logout URL**..


   d. Select **Save Changes**.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

### Create IdeaScale test user

To enable Microsoft Entra users to log into IdeaScale, they must be provisioned in to IdeaScale. In the case of IdeaScale, provisioning is a manual task.

**To configure user provisioning, perform the following steps:**

1. Log in to your **IdeaScale** company site as administrator.
2. Go to **Community Settings**.

   ![Community Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790847.png "Community Settings")

3. Go to **Basic Settings** > **Member Management**.
4. Select **Add Member**.

   ![Member Management](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790852.png "Member Management")

5. In the Add New Member section, perform the following steps:

   ![Add New Member](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideascale-tutorial/ic790853.png "Add New Member")


   a. In the **Email Addresses** textbox, type the email address of a valid Microsoft Entra account you want to provision.


   b. Select **Save Changes**.


   Note


   The Microsoft Entra account holder gets an email with a link to confirm the account before it becomes active.

Note

You can use any other IdeaScale user account creation tools or APIs provided by IdeaScale to provision Microsoft Entra user accounts.

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the IdeaScale tile in the Access Panel, you should be automatically signed in to the IdeaScale for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
