<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/performancecentre-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure PerformanceCentre for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate PerformanceCentre with Microsoft Entra ID. Integrating PerformanceCentre with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to PerformanceCentre.
- You can enable your users to be automatically signed-in to PerformanceCentre \(Single Sign-On\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on). If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- PerformanceCentre single sign-on enabled subscription

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- PerformanceCentre supports **SP** initiated SSO

## Adding PerformanceCentre from the gallery

To configure the integration of PerformanceCentre into Microsoft Entra ID, you need to add PerformanceCentre from the gallery to your list of managed SaaS apps.

**To add PerformanceCentre from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **PerformanceCentre**, select **PerformanceCentre** from result panel then select **Add** button to add the application.

   ![PerformanceCentre in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with PerformanceCentre based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in PerformanceCentre needs to be established.

To configure and test Microsoft Entra single sign-on with PerformanceCentre, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure PerformanceCentre Single Sign-On](#configure-performancecentre-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create PerformanceCentre test user](#create-performancecentre-test-user)** - to have a counterpart of Britta Simon in PerformanceCentre that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with PerformanceCentre, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **PerformanceCentre** application integration page, select **Single sign-on**.

   ![Configure single sign-on link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   ![PerformanceCentre Domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/sp-identifier.png)


   a. In the **Sign on URL** text box, type a URL using the following pattern: `http://<companyname>.performancecentre.com/saml/SSO`


   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `http://<companyname>.performancecentre.com`


   Note


   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [PerformanceCentre Client support team](https://www.performio.co/contact-us) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up PerformanceCentre** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)


   a. Login URL


   b. Microsoft Entra Identifier


   c. Logout URL

### Configure PerformanceCentre Single Sign-On

1. Sign-on to your **PerformanceCentre** company site as administrator.
2. In the tab on the left side, select **Configure**.

   ![Screenshot that shows the "PerformanceCenter" menu with "Configure" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_06.png)

3. In the tab on the left side, select **Miscellaneous**, and then select **Single Sign On**.

   ![Screenshot that shows the "Configure" tab with "Single Sign-On" selected from the "Miscellaneous" menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_07.png)

4. As **Protocol**, select **SAML**.

   ![Screenshot that shows the "Single Sign-On Configuration" section with "S A M L" selected from the "Protocol" menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_08.png)

5. Open your downloaded metadata file in notepad, copy the content, paste it into the **Identity Provider Metadata** textbox, and then select **Save**.

   ![Screenshot that shows the "Identity Provider Metadata" textbox.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_09.png)

6. Verify that the values for the **Entity Base URL** and **Entity ID URL** are correct.

   ![Microsoft Entra Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_10.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

### Create PerformanceCentre test user

The objective of this section is to create a user called Britta Simon in PerformanceCentre.

**To create a user called Britta Simon in PerformanceCentre, perform the following steps:**

1. Sign on to your PerformanceCentre company site as administrator.
2. In the menu on the left, select **Interrelate**, and then select **Create Participant**.

   ![Screenshot that shows the "PerformanceCenter" company site "Interrelate -Participants" page with the "Create Participant" button selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_11.png)

3. On the **Interrelate - Create Participant** dialog, perform the following steps:

   ![Create User](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/performancecentre-tutorial/tutorial_performancecentre_12.png)


   a. Type the required attributes for Britta Simon into related textboxes.


   Important


   Britta's User Name attribute in PerformanceCentre must be the same as the User Name in Microsoft Entra ID.


   b. Select **Client Administrator** as **Choose Role**.


   c. Select **Save**.

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the PerformanceCentre tile in the Access Panel, you should be automatically signed in to the PerformanceCentre for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
