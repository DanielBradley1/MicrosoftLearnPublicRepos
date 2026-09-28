<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/acoustic-connect-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Acoustic Connect for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Acoustic Connect with Microsoft Entra ID. Acoustic Connect is platform that helps you create marketing campaigns that resonate with people, build a loyal following, and drive revenue. When you integrate Acoustic Connect with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Acoustic Connect.
- Enable your users to be automatically signed-in to Acoustic Connect with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Acoustic Connect in a test environment. Acoustic Connect supports both **SP** and **IDP** initiated single sign-on and **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with Acoustic Connect, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Acoustic Connect single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Acoustic Connect application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Acoustic Connect from the Microsoft Entra gallery

Add Acoustic Connect from the Microsoft Entra application gallery to configure single sign-on with Acoustic Connect. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Acoustic Connect** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://www.okta.com/saml2/service-provider/<Acoustic_ID>`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://login.goacoustic.com/sso/saml2/<ID>`
6. Perform the following step, if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** textbox, type the URL: `https://login.goacoustic.com/`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Acoustic Connect support team](mailto:support@acoustic.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

8. On the **Set up Acoustic Connect** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Attributes")

## Configure Acoustic Connect SSO

To configure single sign-on on **Acoustic Connect** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Acoustic Connect support team](mailto:support@acoustic.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Acoustic Connect test user

In this section, a user called B.Simon is created in Acoustic Connect. Acoustic Connect supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Acoustic Connect, a new one is commonly created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Acoustic Connect Sign-on URL where you can initiate the login flow.
- Go to Acoustic Connect Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Acoustic Connect for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Acoustic Connect tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Acoustic Connect for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Acoustic Connect you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
