<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/juno-journey-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Juno Journey for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Juno Journey with Microsoft Entra ID. When you integrate Juno Journey with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Juno Journey.
- Enable your users to be automatically signed-in to Juno Journey with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Juno Journey single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Juno Journey supports **SP and IDP** initiated SSO.
- Juno Journey supports **Just In Time** user provisioning.
- Juno Journey supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/juno-journey-provisioning-tutorial).

## Adding Juno Journey from the gallery

To configure the integration of Juno Journey into Microsoft Entra ID, you need to add Juno Journey from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Juno Journey** in the search box.
4. Select **Juno Journey** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Juno Journey

Configure and test Microsoft Entra SSO with Juno Journey using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Juno Journey.

To configure and test Microsoft Entra SSO with Juno Journey, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Juno Journey SSO](#configure-juno-journey-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Juno Journey test user](#create-juno-journey-test-user)** - to have a counterpart of B.Simon in Juno Journey that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Juno Journey** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<tenant-subdomain>.the-juno.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<tenant-subdomain>.the-juno.com/sso/saml/login`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<tenant-subdomain>.the-juno.com/sso/saml/login`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Juno Journey Client support team](mailto:support@the-juno.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

8. On the **Set up Juno Journey** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Juno Journey SSO

To configure single sign-on on **Juno Journey** side, you need to send the downloaded **Certificate \(Raw\)** and appropriate copied URLs from the application configuration to [Juno Journey support team](mailto:support@the-juno.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Juno Journey test user

In this section, a user called B.Simon is created in Juno Journey. Juno Journey supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Juno Journey, a new one is created after authentication.

Juno Journey also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/juno-journey-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Juno Journey Sign on URL where you can initiate the login flow.
- Go to Juno Journey Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Juno Journey for which you set up the SSO

You can also use Microsoft My Apps to test the application in any mode. When you select the Juno Journey tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Juno Journey for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Juno Journey you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
