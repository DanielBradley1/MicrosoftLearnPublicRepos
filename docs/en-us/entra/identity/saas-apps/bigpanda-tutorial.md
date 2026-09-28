<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/bigpanda-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure BigPanda for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate BigPanda with Microsoft Entra ID. BigPanda transforms IT data into actionable intelligence and automation, enabling incident response teams to increase uptime, efficiency, and velocity. When you integrate BigPanda with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to BigPanda.
- Enable your users to be automatically signed-in to BigPanda with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for BigPanda in a test environment. BigPanda supports both **SP** and **IDP** initiated single sign-on and **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with BigPanda, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- A BigPanda account with the Single Sign On role set to Full Access. See [Roles and Resource Permissions](https://docs.bigpanda.io/docs/roles-management#roles-and-resource-permissions) in the BigPanda documentation for more information.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the BigPanda application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add BigPanda from the Microsoft Entra gallery

Add BigPanda from the Microsoft Entra application gallery to configure single sign-on with BigPanda. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **BigPanda** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type the URL: `https://bigpanda.io/SAML2`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://api.bigpanda.io/login/<ORG_NAME>/azure/callback`
6. If you wish to configure the application in **SP** initiated mode, then perform the following step:

   In the **Sign on URL** textbox, type a URL using the following pattern: `https://api.bigpanda.io/login/<INSTANCE>`

   Note

   These values aren't real. Update these values with the actual Reply URL and Sign on URL. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the file and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

8. On the **Set up BigPanda** section, copy the **Login URL**.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

## Configure BigPanda SSO

To configure single sign-on on **BigPanda** side, please follow the instructions from [BigPanda documentation](https://docs.bigpanda.io/en/microsoft-entra-id--formerly-azure-ad-).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to BigPanda Sign-on URL where you can initiate the login flow.
- Go to BigPanda Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the BigPanda for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the BigPanda tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the BigPanda for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure BigPanda you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
