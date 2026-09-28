<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/axway-csos-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Axway CSOS for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Axway CSOS with Microsoft Entra ID. When you integrate Axway CSOS with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Axway CSOS.
- Enable your users to be automatically signed-in to Axway CSOS with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Axway CSOS single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Axway CSOS supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Axway CSOS from the gallery

To configure the integration of Axway CSOS into Microsoft Entra ID, you need to add Axway CSOS from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Axway CSOS** in the search box.
4. Select **Axway CSOS** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Axway CSOS

Configure and test Microsoft Entra SSO with Axway CSOS using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Axway CSOS.

To configure and test Microsoft Entra SSO with Axway CSOS, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Axway CSOS SSO](#configure-axway-csos-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Axway CSOS test user](#create-axway-csos-test-user)** - to have a counterpart of B.Simon in Axway CSOS that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Axway CSOS** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the URL: `https://www.axway.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<host>:<port>/ui/core/SsoSamlAssertionConsumer`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<host>:<port>/ui`

   Note

   These values aren't real. Update these values with the actual Reply URL and Sign-on URL. Contact [Axway CSOS Client support team](mailto:support@axway.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Axway CSOS** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Axway CSOS SSO

To configure single sign-on on **Axway CSOS** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Axway CSOS support team](mailto:support@axway.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Axway CSOS test user

In this section, you create a user called Britta Simon in Axway CSOS. Work with [Axway CSOS support team](mailto:support@axway.com) to add the users in the Axway CSOS platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Axway CSOS Sign-on URL where you can initiate the login flow.
- Go to Axway CSOS Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Axway CSOS tile in the My Apps, this option redirects to Axway CSOS Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Axway CSOS you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
