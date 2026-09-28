<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/hub-planner-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Hub Planner for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Hub Planner with Microsoft Entra ID. When you integrate Hub Planner with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Hub Planner.
- Enable your users to be automatically signed-in to Hub Planner with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Hub Planner single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Hub Planner supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Hub Planner from the gallery

To configure the integration of Hub Planner into Microsoft Entra ID, you need to add Hub Planner from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Hub Planner** in the search box.
4. Select **Hub Planner** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Hub Planner

Configure and test Microsoft Entra SSO with Hub Planner using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Hub Planner.

To configure and test Microsoft Entra SSO with Hub Planner, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Hub Planner SSO](#configure-hub-planner-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Hub Planner test user](#create-hub-planner-test-user)** - to have a counterpart of B.Simon in Hub Planner that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Hub Planner** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** box, type a URL using the following pattern: `https://app.hubplanner.com/sso/metadata`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://app.hubplanner.com/sso/callback`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.hubplanner.com`

   Note

   These values are the ones you use. The only change you need to make is to replace <SUBDOMAIN> in the **Sign-on URL** with the subdomain you received when you signed up for Hub Planner. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Hub Planner** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Hub Planner SSO

To configure single sign-on on **Hub Planner** side, you need to sign in to your Hub Planner account and complete the following tasks.

### Install the extension in Hub Planner

To enable SSO functionality, you must first enable the extension. As the account owner or with equivalent permissions, complete these steps:

1. Go to **Settings**.
2. In the side menu, select **Manage Extensions** > **Add/Remove Extensions**.
3. Find the extension for Single Sign On and Add or Try Free.
4. When prompted, agree to the terms and conditions, and then select **Add Now**.

### Enable SSO

After the extension is enabled, you must enable SSO for your account.

1. Go to **Settings**.
2. In the side menu, select **Authentication**.
3. Select **SSO \(Single Sign-On\)**.
4. For **SAML 2.0 Endpoint URL\(HTTP\)**, enter your **Login URL**.
5. For **Identity Provider Issuer**, enter your Microsoft Entra identifier.
6. For **X.509 certificate**, enter your certificate.
7. Select **Save**.

### Create Hub Planner test user

If you want to add other users go to **Settings** > **Manage resources** and add users from here. Make sure to add their email address and invite them. Once invited, they will receive an email and be able to enter via SSO.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Hub Planner Sign-on URL where you can initiate the login flow.
- Go to Hub Planner Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Hub Planner tile in the My Apps, this option redirects to Hub Planner Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Hub Planner you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
