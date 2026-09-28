<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/trevanna-tracks-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Trevanna Tracks for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Trevanna Tracks with Microsoft Entra ID. When you integrate Trevanna Tracks with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Trevanna Tracks.
- Enable your users to be automatically signed-in to Trevanna Tracks with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Trevanna Tracks single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Trevanna Tracks supports only **SP** initiated SSO.

## Add Trevanna Tracks from the gallery

To configure the integration of Trevanna Tracks into Microsoft Entra ID, you need to add Trevanna Tracks from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Trevanna Tracks** in the search box.
4. Select **Trevanna Tracks** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Trevanna Tracks

Configure and test Microsoft Entra SSO with Trevanna Tracks using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Trevanna Tracks.

To configure and test Microsoft Entra SSO with Trevanna Tracks, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Trevanna Tracks SSO](#configure-trevanna-tracks-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Trevanna Tracks test user](#create-trevanna-tracks-test-user)** - to have a counterpart of B.Simon in Trevanna Tracks that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Trevanna Tracks** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `http://www.okta.com/<Trevanna_ID>`

   b. In the **Reply URL** text box, type the URL: `https://api.trevannatracks.com/api/v1/authentication/sso/entra`

   c. In the **Sign on URL** text box, type the URL: `https://app.trevannatracks.com/auth/login`

   Note

   The Identifier value isn't real. Update the value with the actual Identifier. Contact [Trevanna Tracks support team](mailto:hello@trevannatracks.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png "Certificate")

7. On the **Set up Trevanna Tracks** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Trevanna Tracks SSO

To configure single sign-on on **Trevanna Tracks** side, you need to send the downloaded **Certificate \(Raw\)** and appropriate copied URLs from Microsoft Entra admin center to [Trevanna Tracks support team](mailto:hello@trevannatracks.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Trevanna Tracks test user

In this section, you create a user called B.Simon in Trevanna Tracks. Work with [Trevanna Tracks support team](mailto:hello@trevannatracks.com) to add the users in the Trevanna Tracks platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Trevanna Tracks Sign-on URL where you can initiate the login flow.
- Go to Trevanna Tracks Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Trevanna Tracks tile in the My Apps, this option redirects to Trevanna Tracks Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Trevanna Tracks you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
