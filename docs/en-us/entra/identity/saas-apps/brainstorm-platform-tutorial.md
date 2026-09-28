<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/brainstorm-platform-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure BrainStorm Platform for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate BrainStorm Platform with Microsoft Entra ID. The BrainStorm Platform empowers end users to personalize their experience, empowering them to embrace long-term behavioral change. When you integrate BrainStorm Platform with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to BrainStorm Platform.
- Enable your users to be automatically signed-in to BrainStorm Platform with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You're able to configure and test Microsoft Entra single sign-on for BrainStorm Platform in your BrainStorm environment. BrainStorm Platform supports only **SP** initiated single sign-on and **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with BrainStorm Platform, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- BrainStorm Platform single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the BrainStorm Platform application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add BrainStorm Platform from the Microsoft Entra gallery

Add BrainStorm Platform from the Microsoft Entra application gallery to configure single sign-on with BrainStorm Platform. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **BrainStorm Platform** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type the value: `urn:brainstorminc:auth:wsfed`

   b. In the **Reply URL** textbox, type the URL: `https://auth.brainstorminc.com/signin-wsfed`

   c. In the **Sign on URL** textbox, type a URL using the following pattern: `https://auth.brainstorminc.com/auth/wsfed?providerId=<ID>`

   Note

   This value isn't real. Update this value with the actual Sign on URL. Contact [BrainStorm Platform Client support team](mailto:support@brainstorminc.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. BrainStorm Platform application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

7. In addition to above, the BrainStorm platform application allows few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | title | user.jobtitle |
   | department | user.department |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure BrainStorm Platform SSO

To configure single sign-on on **BrainStorm Platform** side, you need to send the **App Federation Metadata Url** to [BrainStorm Platform support team](mailto:support@brainstorminc.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create BrainStorm Platform test user

In this section, a user called B.Simon is created in BrainStorm Platform. BrainStorm Platform supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in BrainStorm Platform, a new one is commonly created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to BrainStorm Platform Sign-on URL where you can initiate the login flow.
- Go to BrainStorm Platform Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the BrainStorm Platform tile in the My Apps, this option redirects to BrainStorm Platform Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure BrainStorm Platform you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
