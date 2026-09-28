<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cosgrid-networks-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Cosgrid Networks for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Cosgrid Networks with Microsoft Entra ID. Cosgrid Networks offers secure and efficient enterprise connections through SD-WAN and SASE solutions. Our flexible architecture transforms your network infrastructure for seamless operations. When you integrate Cosgrid Networks with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Cosgrid Networks.
- Enable your users to be automatically signed-in to Cosgrid Networks with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You configure and test Microsoft Entra single sign-on for Cosgrid Networks in a test environment. Cosgrid Networks supports **SP** initiated single sign-on.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with Cosgrid Networks, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Cosgrid Networks single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Cosgrid Networks application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Cosgrid Networks from the Microsoft Entra gallery

Add Cosgrid Networks from the Microsoft Entra application gallery to configure single sign-on with Cosgrid Networks. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cosgrid Networks** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type the URL: `https://cosgridnetworks.in/api/v1/auth/acs/`

   b. In the **Reply URL** textbox, type the URL: `https://cosgridnetworks.in/api/v1/auth/acs/`

   c. In the **Sign on URL** textbox, type the URL: `https://www.cosgrid.net/auth/login`
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure Cosgrid Networks SSO

To configure single sign-on on **Cosgrid Networks** side, you need to send the **App Federation Metadata Url** to [Cosgrid Networks support team](mailto:contact@cosgrid.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Cosgrid Networks test user

In this section, you create a user called Britta Simon at Cosgrid Networks. Work with [Cosgrid Networks support team](mailto:contact@cosgrid.com) to add the users in the Cosgrid Networks platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Cosgrid Networks Sign-on URL where you can initiate the login flow.
- Go to Cosgrid Networks Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Cosgrid Networks tile in the My Apps, this option redirects to Cosgrid Networks Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Cosgrid Networks you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
