<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/samsung-knox-and-business-services-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Samsung Knox and Business Services for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Samsung Knox and Business Services with Microsoft Entra ID. When you integrate Samsung Knox and Business Services with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Samsung Knox and Business Services.
- Enable your users to be automatically signed-in to Samsung Knox and Business Services with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Samsung Knox account.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Samsung Knox and Business Services support only **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Samsung Knox and Business Services from the gallery

To configure the integration of Samsung Knox and Business Services into Microsoft Entra ID, you need to add Samsung Knox and Business Services from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Samsung Knox and Business Services** in the search box.
4. Select **Samsung Knox and Business Services** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Samsung Knox and Business Services

Configure and test Microsoft Entra SSO with Samsung Knox and Business Services using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in [SamsungKnox.com](https://samsungknox.com/).

To configure and test Microsoft Entra SSO with Samsung Knox and Business Services, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Samsung Knox and Business Services SSO](#configure-samsung-knox-and-business-services-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Samsung Knox and Business Services test user](#create-samsung-knox-and-business-services-test-user)** - to have a counterpart of B.Simon in Samsung Knox and Business Services that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Samsung Knox and Business Services** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Identifier \(Entity ID\)** text box, type the URL: `https://www.samsungknox.com/`

   b. In the **Reply URL** text box, type the URL: `https://central.samsungknox.com/ams/ad/saml/acs`

   c. In the **Sign on URL** text box, type the URL: `https://account.samsung.com/`
6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Samsung Knox and Business Services SSO

1. In a different web browser window, sign in to [SamsungKnox.com](https://samsungknox.com/) as an administrator.
2. Select the **Avatar** on the top right corner.

   ![Samsung Knox avatar](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/samsung-knox-and-business-services-tutorial/avatar.png)

3. Go to **My account** > **SSO SETTINGS** and perform the following steps.

   ![Screenshot shows the Samsung knox settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/samsung-knox-and-business-services-tutorial/settings.png "Settings")


   a. In the **Identifier \(entity ID\)** text box, paste the **Identifier** URL which you have copied from the Microsoft Entra admin center.


   b. Copy **Reply URL \(assertion consumer service URL\)** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section in Microsoft Entra admin center.


   c. In the **App federation metadata URL** text box, paste the **App federation metadata URL** which you have copied From the Microsoft Entra admin center.


   d. Select **CONNECT TO SSO**.

### Create Samsung Knox and Business Services test user

In this section, you create a user called Britta Simon in Samsung Knox and Business Services. Refer to the [Knox Configure](https://docs.samsungknox.com/admin/knox-configure/Administrators.htm) or [Knox Mobile Enrollment](https://docs.samsungknox.com/admin/knox-mobile-enrollment/kme-add-an-admin.htm) admin guides for instructions on how to invite a subadministrator, or test user, to your Samsung Knox organization. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to [SamsungKnox.com](https://samsungknox.com/), where you can initiate the login flow.
- Go to [SamsungKnox.com](https://samsungknox.com/) directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Samsung Knox and Business Services tile in the My Apps, this option redirects to [SamsungKnox.com](https://samsungknox.com/). For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Samsung Knox and Business Services you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
