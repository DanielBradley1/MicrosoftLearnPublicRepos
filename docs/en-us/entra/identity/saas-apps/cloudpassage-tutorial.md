<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cloudpassage-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure CloudPassage for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate CloudPassage with Microsoft Entra ID. When you integrate CloudPassage with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to CloudPassage.
- Enable your users to be automatically signed in to CloudPassage with their Microsoft Entra accounts.
- Manage your accounts in one central location.

To learn more about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- CloudPassage single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- CloudPassage supports **SP** initiated SSO

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding CloudPassage from the gallery

To configure the integration of CloudPassage into Microsoft Entra ID, you need to add CloudPassage from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **CloudPassage** in the search box.
4. Select **CloudPassage** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra single sign-on for CloudPassage

Configure and test Microsoft Entra SSO with CloudPassage using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in CloudPassage.

To configure and test Microsoft Entra SSO with CloudPassage, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure CloudPassage SSO](#configure-cloudpassage-sso)** - to configure the single sign-on settings on application side.

   1. **[Create CloudPassage test user](#create-cloudpassage-test-user)** - to have a counterpart of B.Simon in CloudPassage that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **CloudPassage** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Sign-on URL** text box, type a URL using the following pattern: `https://portal.cloudpassage.com/saml/init/accountid`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://portal.cloudpassage.com/saml/consume/accountid`. You can get your value for this attribute by selecting **SSO Setup documentation** in the **Single Sign-on Settings** section of your CloudPassage portal.

   ![Screenshot shows the CloudPassage portal with the S S O Setup Documentation link called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_05.png)


   Note


   These values aren't real. Update these values with the actual Sign-On URL and Reply URL. Contact [CloudPassage Client support team](https://fidelissecurity.com/contact/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. CloudPassage application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png)

7. In addition to above, CloudPassage application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirement.
   | Name | Source Attribute |
   | --- | --- |
   | firstname | user.givenname |
   | lastname | user.surname |
   | email | user.mail |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

9. On the **Set up CloudPassage** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure CloudPassage SSO

1. In a different browser window, sign-on to your CloudPassage company site as administrator.
2. In the menu on the top, select **Settings**, and then select **Site Administration**.

   ![Screenshot shows the CloudPassage site with Site Administration selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_07.png)

3. Select the **Authentication Settings** tab.

   ![Screenshot shows the CloudPassage site with the Authentication Settings tab selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_08.png)

4. In the **Single Sign-on Settings** section, perform the following steps:

   ![Screenshot shows the Single Sign-on Settings section where you can enter the information in this step.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_09.png)


   a. Select **Enable Single sign-on\(SSO\)\(SSO Setup Documentation\)** checkbox.


   b. Paste **Microsoft Entra Identifier** into the **SAML issuer URL** textbox.


   c. Paste **Login URL** into the **SAML endpoint URL** textbox.


   d. Paste **Logout URL** into the **Logout landing page** textbox.


   e. Open your downloaded certificate in notepad, copy the content of downloaded certificate into your clipboard, and then paste it into the **x 509 certificate** textbox.


   f. Select **Save**.

### Create CloudPassage test user

The objective of this section is to create a user called B.Simon in CloudPassage.

**To create a user called B.Simon in CloudPassage, perform the following steps:**

1. Sign-on to your **CloudPassage** company site as an administrator.
2. In the toolbar on the top, select **Settings**, and then select **Site Administration**.

   ![Screenshot shows CloudPassage with Site Administration selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_15.png)

3. Select the **Users** tab, and then select **Add New User**.

   ![Screenshot shows CloudPassage Site Administration with the Users tab selected and the option to Add New User.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_16.png)

4. In the **Add New User** section, perform the following steps:

   ![Screenshot shows the Add New User section where you can specify user information.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cloudpassage-tutorial/tutorial_cloudpassage_17.png)


   a. In the **First Name** textbox, type Britta.


   b. In the **Last Name** textbox, type Simon.


   c. In the **Username** textbox, the **Email** textbox and the **Retype Email** textbox, type Britta's user name in Microsoft Entra ID.


   d. As **Access Type**, select **Enable Halo Portal Access**.


   e. Select **Add**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the CloudPassage tile in the Access Panel, you should be automatically signed in to the CloudPassage for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
