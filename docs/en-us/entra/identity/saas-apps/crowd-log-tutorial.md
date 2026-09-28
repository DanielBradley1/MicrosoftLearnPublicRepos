<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/crowd-log-tutorial -->
<!-- Sitemap-Last-Modified: 2026-02-19 -->

# Configure Crowd Log for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Crowd Log with Microsoft Entra ID. When you integrate Crowd Log with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Crowd Log.
- Enable your users to be automatically signed-in to Crowd Log with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Crowd Log single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Crowd Log supports **SP and IDP** initiated SSO.

## Add Crowd Log from the gallery

To configure the integration of Crowd Log into Microsoft Entra ID, you need to add Crowd Log from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Crowd Log** in the search box.
4. Select **Crowd Log** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Crowd Log

Configure and test Microsoft Entra SSO with Crowd Log using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Crowd Log.

To configure and test Microsoft Entra SSO with Crowd Log, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Crowd Log SSO](#configure-crowd-log-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Crowd Log test user](#create-crowd-log-test-user)** - to have a counterpart of B.Simon in Crowd Log that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Crowd Log** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://app.crowdlog.jp/metadata/<auth_code>/`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://app.crowdlog.jp/saml/?auth_code=<auth_code>`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://app.crowdlog.jp/login.cgi?auth_code=<auth_code>`

   Note

   These values aren't real. Check the actual Identifier, Reply URL and Sign-on URL on the "Company Settings > Security > SAML Auth" on Crowd Log. You can also refer to the patterns shown in the Basic SAML Configuration section.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Crowd Log SSO

To perform the Single Sign-On configuration on the Crowd Log side, please refer to the Crowd Log SAML admin settings documentation.

### Create Crowd Log test user

In this section, you create a user called Britta Simon in Crowd Log. For more information on how to create a user, please refer to the Crowd Log member creation documentation.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Crowd Log Sign on URL where you can initiate the login flow.
- Go to Crowd Log Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Crowd Log for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Crowd Log tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Crowd Log for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Crowd Log you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
