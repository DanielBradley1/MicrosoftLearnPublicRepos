<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/sauce-labs-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Sauce Labs for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Sauce Labs with Microsoft Entra ID. App integration for single sign-on and automatic account provisioning at Sauce Labs. When you integrate Sauce Labs with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Sauce Labs.
- Enable your users to be automatically signed-in to Sauce Labs with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You configure and test Microsoft Entra single sign-on for Sauce Labs in a test environment. Sauce Labs supports both **SP** and **IDP** initiated single sign-on and **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant. If your company has more than one organization at Sauce Labs to be integrated with SAML SSO within a single Azure tenant, please refer to the following [documentation](https://docs.saucelabs.com/basics/sso/setting-up-sso-special-cases/#single-identity-provider-and-multiple-organizations-at-sauce-labs).

## Prerequisites

To integrate Microsoft Entra ID with Sauce Labs, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Sauce Labs single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Sauce Labs application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Sauce Labs from the Microsoft Entra gallery

Add Sauce Labs from the Microsoft Entra application gallery to configure single sign-on with Sauce Labs. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Sauce Labs** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already preintegrated with Azure.
6. If you wish to configure the application in **SP** initiated mode, then perform the following step:

   In the **Sign on URL** textbox, type the URL: `https://accounts.saucelabs.com/`
7. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

8. On the **Set up Sauce Labs** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

## Configure Sauce Labs SSO

To configure single sign-on on Sauce Labs side, please refer this [documentation](https://docs.saucelabs.com/basics/sso/setting-up-sso/#integrating-with-sauce-labs-service-provider) to set up SAML SSO connection properly on both sides. For any help or queries, please contact [Sauce Labs support team](mailto:support@saucelabs.com).

### Create Sauce Labs test user

In this section, a user called B.Simon is created in Sauce Labs. Sauce Labs supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Sauce Labs, a new one is commonly created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Sauce Labs Sign-on URL where you can initiate the login flow.
- Go to Sauce Labs Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Sauce Labs for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Sauce Labs tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Sauce Labs for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Sauce Labs you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
