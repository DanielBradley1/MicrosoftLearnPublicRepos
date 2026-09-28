<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/new-relic-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure New Relic by Account for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate New Relic by Account with Microsoft Entra ID. When you integrate New Relic by Account with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to New Relic by Account.
- Enable your users to be automatically signed-in to New Relic by Account with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Note

This document is only relevant if you're using the [Original User Model](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/overview-user-models/) in New Relic. Please refer to [New Relic \(By Organization\)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/new-relic-limited-release-tutorial) if you're using New Relic's newer user model.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- New Relic by Account single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- New Relic by Account supports **SP** initiated SSO
- New Relic supports [**automated user provisioning and deprovisioning**](https://learn.microsoft.com/en-us/entra/identity/saas-apps/new-relic-by-organization-provisioning-tutorial) \(recommended\).

## Add New Relic by Account from the gallery

To configure the integration of New Relic by Account into Microsoft Entra ID, you need to add New Relic by Account from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **New Relic by Account** in the search box.
4. Select **New Relic by Account** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for New Relic by Account

Configure and test Microsoft Entra SSO with New Relic by Account using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in New Relic by Account.

To configure and test Microsoft Entra SSO with New Relic by Account, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   - **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   - **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure New Relic by Account SSO](#configure-new-relic-by-account-sso)** - to configure the single sign-on settings on application side.

   - **[Create New Relic by Account test user](#create-new-relic-by-account-test-user)** - to have a counterpart of B.Simon in New Relic by Account that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New Relic by Account** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign on URL** text box, type the URL using the following pattern:

   `https://rpm.newrelic.com:443/accounts/{acc_id}/sso/saml/finalize` - Be sure to substitute `acc_id` with your own Account ID of New Relic by Account.

   b. In the **Identifier \(Entity ID\)** text box, type the URL: `rpm.newrelic.com`
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up New Relic by Account** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure New Relic by Account SSO

1. In a different web browser window, sign on to your **New Relic by Account** company site as administrator.
2. In the menu on the top, select **Account Settings**.

   ![Screenshot shows the Welcome page with Account settings selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/new-relic-tutorial/settings.png "Account Settings")

3. Select the **Security and authentication** tab, and then select the **Single sign on** tab.

   ![Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/new-relic-tutorial/single-sign-on-tab.png "Single Sign-On")

4. On the SAML dialog page, perform the following steps:

   ![SAML](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/new-relic-tutorial/save.png "SAML")


   a. Select **Choose File** to upload your downloaded Microsoft Entra certificate.


   b. In the **Remote login URL** textbox, paste the value of **Login URL**.


   c. In the **Logout landing URL** textbox, paste the value of **Logout URL**.


   d. Select **Save my changes**.

### Create New Relic by Account test user

1. Sign into your **New Relic by Account** company site as administrator.
2. In the menu on the top, select **Account Settings**.

   ![Screenshot shows Account settings selected from the Welcome page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/new-relic-tutorial/account.png "Account Settings")

3. In the **Account** pane on the left side, select **Summary**, and then select **Add user**.

   ![Screenshot shows the Summary pane where you can select Add user.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/new-relic-tutorial/add.png "Account Settings")

4. On the **Active users** dialog, perform the following steps:

   ![Active Users](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/new-relic-tutorial/user.png "Active Users")


   a. In the **Email** textbox, type the email address of a valid Microsoft Entra user you want to provision.


   b. As **Role** select **User**.


   c. Select **Add this user**.

Note

You can use any other New Relic by Account user account creation tools or APIs provided by New Relic by Account to provision Microsoft Entra user accounts.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to New Relic by Account Sign-on URL where you can initiate the login flow.
- Go to New Relic by Account Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the New Relic by Account tile in the My Apps, this option redirects to New Relic by Account Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure New Relic by Account you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
