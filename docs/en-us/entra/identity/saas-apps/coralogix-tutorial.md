<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/coralogix-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Coralogix for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Coralogix with Microsoft Entra ID. When you integrate Coralogix with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Coralogix.
- Enable your users to be automatically signed-in to Coralogix with their Microsoft Entra accounts.
- Manage your accounts in one central location.

To learn more about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Coralogix single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Coralogix supports **SP** initiated SSO

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Coralogix from the gallery

To configure the integration of Coralogix into Microsoft Entra ID, you need to add Coralogix from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Coralogix** in the search box.
4. Select **Coralogix** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra single sign-on for Coralogix

Configure and test Microsoft Entra SSO with Coralogix using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Coralogix.

To configure and test Microsoft Entra SSO with Coralogix, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Coralogix SSO](#configure-coralogix-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Coralogix test user](#create-coralogix-test-user)** - to have a counterpart of B.Simon in Coralogix that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Coralogix** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Sign on URL** box, enter a URL with the following pattern: `https://<SUBDOMAIN>.coralogix.com`

   b. In the **Identifier \(Entity ID\)** text box, enter a URL, such as:

   `https://api.coralogix.com/saml/metadata.xml`

   or

   `https://aws-client-prod.coralogix.com/saml/metadata.xml`

   Note

   The sign-on URL value isn't real. Update the value with the actual sign-on URL. Contact the [Coralogix Client support team](mailto:info@coralogix.com) to get the value. You can also refer to the patterns in the **Basic SAML Configuration** section.
6. The Coralogix application expects the SAML assertions in a specific format. Configure the following claims for this application. You can manage the values of these attributes from the **User Attributes** section on the application integration page. On the **Set up Single Sign-On with SAML** page, select the **Edit** button to open the **User Attributes** dialog box.

   ![Screenshot that shows the "User Attributes" dialog with the "Edit" button highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png)

7. In the **User Claims** section in the **User Attributes** dialog box, edit the claims by using the **Edit** icon. You can also add the claims by using **Add new claim** to configure the SAML token attribute as shown in the previous image. Then take the following steps:

   a. Select the **Edit icon** to open the **Manage user claims** dialog box.

   ![Screenshot that shows the "User Attributes & Claims" dialog with the "Edit" button highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/coralogix-tutorial/tutorial_usermail.png) ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/coralogix-tutorial/tutorial_usermailedit.png)

   b. From the **Choose name identifier format** list, select **Email address**.

   c. From the **Source attribute** list, select **user.mail**.

   d. Select **Save**.
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

9. On the **Set up Coralogix** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Coralogix SSO

To configure single sign-on on **Coralogix** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Coralogix support team](mailto:info@coralogix.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Coralogix test user

In this section, you create a user called Britta Simon in Coralogix. Work with [Coralogix support team](mailto:info@coralogix.com) to add the users in the Coralogix platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Coralogix tile in the Access Panel, you should be automatically signed in to the Coralogix for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
