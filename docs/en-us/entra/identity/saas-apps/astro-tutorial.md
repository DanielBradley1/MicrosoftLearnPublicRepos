<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/astro-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Astro for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Astro with Microsoft Entra ID. When you integrate Astro with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Astro.
- Enable your users to be automatically signed-in to Astro with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Astro single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Astro supports both **SP and IDP** initiated SSO.
- Astro supports **Just In Time** user provisioning.

## Add Astro from the gallery

To configure the integration of Astro into Microsoft Entra ID, you need to add Astro from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Astro** in the search box.
4. Select **Astro** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Astro

Configure and test Microsoft Entra SSO with Astro using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Astro.

To configure and test Microsoft Entra SSO with Astro, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Astro SSO](#configure-astro-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Astro test user](#create-astro-test-user)** - to have a counterpart of B.Simon in Astro that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Astro** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the value using the following pattern: `urn:auth0:astronomer-prod:samlp-<ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://auth.astronomer.io/login/callback?connection=samlp-<ID>`
6. Perform the following step, if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://cloud.astronomer.io/login`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Astro support team](mailto:support@astronomer.io) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(PEM\)** and select **PEM certificate download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificate-base64-download.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Astro SSO

To configure single sign-on on **Astro** side, you need to send the downloaded **Certificate \(PEM\)** and appropriate copied URLs from Microsoft Entra admin center to [Astro support team](mailto:support@astronomer.io). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Astro test user

In this section, a user called Britta Simon is created in Astro. Astro supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Astro, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Astro Sign on URL where you can initiate the login flow.
- Go to Astro Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application** in Microsoft Entra admin center and you should be automatically signed in to the Astro for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Astro tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Astro for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Astro you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
