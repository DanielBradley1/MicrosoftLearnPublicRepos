<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/exium-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Exium for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Exium with Microsoft Entra ID. When you integrate Exium with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Exium.
- Enable your users to be automatically signed-in to Exium with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Exium single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Exium supports **SP** initiated SSO.
- Exium supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/exium-provisioning-tutorial).

## Adding Exium from the gallery

To configure the integration of Exium into Microsoft Entra ID, you need to add Exium from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Exium** in the search box.
4. Select **Exium** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Exium

Configure and test Microsoft Entra SSO with Exium using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Exium.

To configure and test Microsoft Entra SSO with Exium, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Exium SSO](#configure-exium-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Exium test user](#create-exium-test-user)** - to have a counterpart of B.Simon in Exium that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Exium** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://subapi.exium.net/saml/<WORKSPACE_ID>/metadata`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://subapi.exium.net/saml/<WORKSPACE_ID>/acs`

   c. In the **Sign on URL** text box, type the URL: `https://service.exium.net/sign-in`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Exium Client support team](mailto:support@exium.net) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Exium SSO

1. Sign in to Exium company site as an administrator.
2. In the **Admin Console**, select **Company Profile** panel.

   ![screenshot for admin console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/exium-tutorial/company-profile.png)

3. In the **Profile**, select **SSO Settings** and **Edit** it.
4. Perform the below steps in the **SSO Settings** section.

   ![screenshot for SSO Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/exium-tutorial/update.png)


   a. Select **SSO Type** as **Microsoft Entra ID** from the dropdown.


   b. Paste the **App Federation Metadata Url** value in the **SAML 2.0 IDP Metadata URL** field.


   c. Copy **SAML 2.0 SSO URL** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section.


   d. Copy **SAML 2.0 SP Entity ID** value, paste this value into the **Identifier** text box in the **Basic SAML Configuration** section.


   e. Select **Update**.

### Create Exium test user

1. Sign in to Exium company site as an administrator.
2. Go to the **User Management -> Users** and select **Add User**.

   ![screenshot for create test user](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/exium-tutorial/add-user.png)

3. Enter the required fields in the following page and select **Save**.

   ![screenshot for create test user fields with save button](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/exium-tutorial/add-user-2.png)

Note

Exium also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/exium-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Exium Sign-on URL where you can initiate the login flow.
- Go to Exium Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Exium tile in the My Apps, this option redirects to Exium Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Exium you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
