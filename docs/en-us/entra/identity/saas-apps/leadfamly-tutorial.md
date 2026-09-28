<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/leadfamly-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Leadfamly for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Leadfamly with Microsoft Entra ID. When you integrate Leadfamly with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Leadfamly.
- Enable your users to be automatically signed-in to Leadfamly with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Leadfamly single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Leadfamly supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Leadfamly from the gallery

To configure the integration of Leadfamly into Microsoft Entra ID, you need to add Leadfamly from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Leadfamly** in the search box.
4. Select **Leadfamly** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Leadfamly

Configure and test Microsoft Entra SSO with Leadfamly using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Leadfamly.

To configure and test Microsoft Entra SSO with Leadfamly, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Leadfamly SSO](#configure-leadfamly-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Leadfamly test user](#create-leadfamly-test-user)** - to have a counterpart of B.Simon in Leadfamly that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Leadfamly** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://appv2.leadfamly.com/saml-sso/<INSTANCE ID>`

   Note

   These values aren't real. Update these values with the actual Sign on URL. Contact [Leadfamly Client support team](mailto:support@leadfamly.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up Leadfamly** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Leadfamly SSO

1. Log in to your Leadfamly company site as an administrator.
2. Go to **Account** ->**Customer information** ->**SAML SSO**.

![Account](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leadfamly-tutorial/configuration.png "Account")

3. Enable **SAML SSO** and select **Microsoft Entra ID** Provider from the dropdown list and perform the following steps.

![Information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leadfamly-tutorial/account.png "Information")

a. Copy **Identifier** value, paste this value into the **Identifier** URL text box in the **Basic SAML Configuration** section.

b. Copy **Reply URL** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section.

c. Copy **Sign on URL** value, paste this value into the **Sign on URL** text box in the **Basic SAML Configuration** section.

d. Open the downloaded **Federation Metadata XML** file into Notepad and upload the content into **Federation Metadata XML**.

e.Select **Save**.

### Create Leadfamly test user

1. In a different web browser window, sign into Leadfamly website as an administrator.
2. Go to **Account** > **Users** > **Invite user**.

![Users Section](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leadfamly-tutorial/users.png "Users Section")

3. Fill the required values in the following fields and select **Save**.

![Modify Users](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leadfamly-tutorial/modify-user.png "Modify Users")

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Leadfamly Sign-on URL where you can initiate the login flow.
- Go to Leadfamly Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Leadfamly tile in the My Apps, this option redirects to Leadfamly Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Leadfamly you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
