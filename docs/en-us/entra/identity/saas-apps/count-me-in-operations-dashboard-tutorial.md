<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/count-me-in-operations-dashboard-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Count Me In - Operations Dashboard for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Count Me In - Operations Dashboard with Microsoft Entra ID. When you integrate Count Me In - Operations Dashboard with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Count Me In - Operations Dashboard.
- Enable your users to be automatically signed-in to Count Me In - Operations Dashboard with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Count Me In - Operations Dashboard single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Count Me In - Operations Dashboard supports **SP** initiated SSO

## Adding Count Me In - Operations Dashboard from the gallery

To configure the integration of Count Me In - Operations Dashboard into Microsoft Entra ID, you need to add Count Me In - Operations Dashboard from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Count Me In - Operations Dashboard** in the search box.
4. Select **Count Me In - Operations Dashboard** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Count Me In - Operations Dashboard

Configure and test Microsoft Entra SSO with Count Me In - Operations Dashboard using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Count Me In - Operations Dashboard.

To configure and test Microsoft Entra SSO with Count Me In - Operations Dashboard, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Count Me In-Operations Dashboard SSO](#configure-count-me-in-operations-dashboard-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Count Me In-Operations Dashboard test user](#create-count-me-in-operations-dashboard-test-user)** - to have a counterpart of B.Simon in Count Me In - Operations Dashboard that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Count Me In - Operations Dashboard** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://api-us.localz.io/user/v1/saml/initsso?projectId=<PROJECT_ID>`

   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `api-us.localz.io/<PROJECT_ID>`

   c. In the **Reply URL** text box, type a URL using the following pattern: `https://api-us.localz.io/user/v1/saml/initsso?projectId=<PROJECT_ID>`

   Note

   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [Count Me In - Operations Dashboard Client support team](mailto:support@localz.co) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Count Me In - Operations Dashboard application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, Count Me In - Operations Dashboard application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | assigned roles | user.assignedroles |


   Note


   Count Me In - Operations Dashboard expects roles for users assigned to the application. Please set up these roles in Microsoft Entra ID so that users can be assigned the appropriate roles. To understand how to configure roles in Microsoft Entra ID, see [here](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-roles-ui).

8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

9. On the **Set up Count Me In - Operations Dashboard** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Count Me In-Operations Dashboard SSO

To configure single sign-on on **Count Me In - Operations Dashboard** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Count Me In - Operations Dashboard support team](mailto:support@localz.co). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Count Me In-Operations Dashboard test user

In this section, you create a user called Britta Simon in Count Me In - Operations Dashboard. Work with [Count Me In - Operations Dashboard support team](mailto:support@localz.co) to add the users in the Count Me In - Operations Dashboard platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Count Me In - Operations Dashboard Sign-on URL where you can initiate the login flow.
- Go to Count Me In - Operations Dashboard Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Count Me In - Operations Dashboard tile in the My Apps, this option redirects to Count Me In - Operations Dashboard Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Count Me In - Operations Dashboard you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
